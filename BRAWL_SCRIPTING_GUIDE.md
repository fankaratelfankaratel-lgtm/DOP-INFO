# Как писать скрипты (.lua / .luau) для Brawl Stars — Null's Mods / NB Scripting

Практическое руководство, собранное по четырём источникам, которые ты дал, плюс разбор рабочих скриптов из библиотеки.

**Что было проверено (фактически скачано и прочитано):**

| Источник | Что внутри | Статус |
|---|---|---|
| [fankaratelfankaratel-lgtm/-CSV-](https://github.com/fankaratelfankaratel-lgtm/-CSV-/tree/main) | `characters.csv` (436 строк), `tiles.csv` (75), `traits.csv` (1242) | прочитано полностью |
| [fankaratelfankaratel-lgtm/SCRIPTS-INFO](https://github.com/fankaratelfankaratel-lgtm/SCRIPTS-INFO/tree/main) | 8 рабочих скриптов (Among Us 77 КБ, Chess 57 КБ, Safe Not Safe 43 КБ, Random Trait 37 КБ, Traffic Light 16 КБ + 3 коротких) | разобраны |
| [nulls-mods-community/scripting-docs](https://github.com/nulls-mods-community/scripting-docs/blob/main/reference.md) | официальный reference API, 542 строки | прочитано полностью |
| [segnpa66-lab/nb-scripts-authors — types.d.luau](https://github.com/segnpa66-lab/nb-scripts-authors/blob/a5e4e428bbc8739eb14380b610be99b01448c2ce/nb-scripting%2Ftypes.d.luau) | 16 991 строка типов, версия `69.252`, все списки имён для `lookup()` | прочитано, извлечены списки |

Дополнительно я сверил CSV с `types.d.luau`: имена из `characters.csv` совпали со списком `CsvName16` (434/436), `tiles.csv` → `CsvName27` (74/75), `traits.csv` → `CsvName108` (1237/1242). То есть **тип 16 = персонажи, 27 = тайлы, 108 = трейты** — подтверждено, а не догадка.

---

## 1. Как устроена среда

Скрипт исполняется **на сервере боя**, а не на клиенте. Это значит:

- ты видишь всё, что происходит в бою, и можешь влиять на всё — позиции, ХП, скиллы, карту, спавн объектов;
- клиент игрока показывает результат автоматически, отдельного «UI-кода» нет — весь «UI» делается через `log()` (чат) и игровые объекты (предметы/спреи/зоны);
- API — это Java-объекты, проброшенные в Luau. Отсюда: методы вызываются через `:` (`char:takeDamage(...)`), поля читаются напрямую (`char.hitPoints`), а `readonly`-поля изменить нельзя — перезапишутся или вызовут ошибку.

Точка входа — **глобальная функция `tick()`**, движок вызывает её каждый тик. Всё, что написано в скрипте вне `tick()`, выполняется один раз при загрузке боя.

Формат важен:

- «чистый» скрипт — просто `.lua`/`.luau` текст с `function tick() ... end`;
- файлы, сгенерированные NB Scripting Tools (как `TrafficLight.lua`), обёрнуты в мини-загрузчик модулей `__NBS_MODULES` / `__NBS_REQUIRE` — эти скрипты собираются из нескольких `.luau` файлов. Писать так не обязательно, но если делаешь большой проект — так удобнее.

## 2. Скелет скрипта и жизненный цикл

```lua
-- ==== ЭТАП ЗАГРУЗКИ (выполняется 1 раз) ====
server.hasIntroSkip = true        -- пропустить интро
server.hasPoisonDisabled = true   -- выключить отравление от сужающейся зоны

local CONFIG = { ... }            -- весь конфиг — наверху, чтобы не искать по коду
local cache = {}                  -- здесь живёт состояние между тиками (таблицы по index/id)

-- дорогие lookup() делаем ОДИН раз, а не каждый тик
local SHELLY_ULTI = lookup(20, "ShotgunGirlUlti")
local WALL        = lookup(27, "Wall1")

-- ==== ЭТАП БОЯ (вызывается каждый тик, ~20 раз в секунду) ====
function tick()
    if server.isBattleEnded then return end      -- защита от работы после конца боя
    if not server:isIntroFinished() then return end -- защита от работы до конца интро

    -- ... логика ...
end
```

Три обязательных проверки в начале `tick()` — они есть почти во всех «взрослых» скриптах библиотеки:

```lua
if server.isBattleEnded then return end            -- бой кончился
if not server:isIntroFinished() then return end    -- интро ещё идёт
if server.playersCount == 0 then return end        -- ещё никто не зашёл
```

## 3. Тики и время

| Единица | Значение |
|---|---|
| 1 тик | 50 мс |
| 20 тиков | 1 секунда |
| 1 минута | 1200 тиков |
| `server.tick` | монотонно растёт на 1 каждые 50 мс |

Хелперы из библиотеки (Among Us / Chess):

```lua
function tickToSecond(t) return t / 20 end
function secondToTick(s) return s * 20 end
```

**Все длительности в API — в тиках.** Если эффект должен держаться 1.5 секунды — это 30 тиков.

**Бюджеты на тик.** Тяжёлую работу нельзя делать целиком в одном тике: сервер лагает, а на слабых картах скрипт крашит бой. В Chess.lua это вынесено в отдельные «ступенчатые» функции:

```lua
local SETUP_PIECES_PER_TICK      = 2   -- расстановка фигур порциями
local CHESS_EFFECT_CHECKS_PER_TICK = 4 -- проверки эффектов порциями
local EVAL_CHECKS_PER_TICK        = 3  -- скан шахматной ситуации порциями
```

Правило: **если цикл длиннее ~200–500 итераций за тик — разбивай его на порции с сохранением позиции в таблице-задании.**

## 4. Карта API

Иерархия объектов:

```
server                                  -- ядро
├── objectManager : GameObjectManager
│   ├── getCharacters()  -> Iterable<LogicCharacter>
│   ├── getProjectiles() -> Iterable<LogicProjectile>
│   ├── getAreaEffects() -> Iterable<LogicAreaEffect>
│   ├── getItems()       -> Iterable<LogicItem>
│   ├── getObject(id)    -> LogicGameObject?
│   └── addObject(obj)
├── map : TileMap
│   ├── getTile(tx, ty) / setDynamicTile(data, tx, ty, owner) / destructTile(tx, ty, isBasic)
│   └── tileSizeX/Y, absSizeX/Y
├── getClientInfo(index) -> ClientInfo?   -- данные игрока
└── tick, playersCount, gameMode, isBattleEnded, hasIntroSkip, hasPoisonDisabled

LogicGameObject (базовый)
├── id, data, x, y, z, index, team, dimension, traits
├── setPosition(x,y,z), isAlive(), getType(), getSkinData(), setIndex(index, team)
└── LogicCharacter  (hp, движение, скиллы, урон, статусы)
    LogicProjectile (finishState, shotCharacter, origin)
    LogicAreaEffect (ownerCharacter, damage, ultiEnergy, trigger, destroy, isObjectInside)
    LogicItem       (sprayDataIndex, isTriggered, triggeredCharacter)
```

`getType()` возвращает: `0` = персонаж, `1` = снаряд, `2` = зона, `3` = предмет.

### ClientInfo — данные игрока

| Поле | Смысл |
|---|---|
| `index`, `team`, `objectId` | номер игрока, команда, id его персонажа |
| `x`, `y` | позиция камеры (обычно = позиция персонажа) |
| `isAlive`, `isBot`, `isRespawning` | живой / бот / возрождается |
| `ultiCharge`, `maxUltiCharge` | заряд супера — **можно писать**: `p.ultiCharge = p.maxUltiCharge` |
| `overchargeCharge`, `maxOverchargeCharge` | гиперзаряд (Overcharge) |
| `ultiUsesLeft`, `isOverchargeActive` | остаток использований супера, активен ли гиперзаряд |
| `gamePoints` | очки (смысл зависит от режима) |
| `emoteUsedIndex`, `emoteUsedTick` | какой эмодзи и на каком тике использован |
| `getSkinData()`, `getAttackTeam()` | скин; «эффективная» команда (важно для Виллоу — иначе игнорируй) |

⚠️ Поля `x`, `y`, `isAlive` обновляются **в конце игрового цикла**. Если ты изменил позицию/ХП, в этом же тике ты увидишь старые значения — проверяй на следующем тике.

### LogicCharacter — основной рабочий класс

**Чтение:** `hitPoints`, `maxHitPoints`, `type` (CharacterType), `angleHead`, `angleLegs` (градусы), `isBot`, `isStunned`, `heroUpgradeLevel`, `linkedCharacter` (мяч), `lastDamageSourceIndex`, `consShieldValue`, `hasRespawnShield`, `dimension` (1 = измерение Корделиуса).

**Запись:** `persistentSpeedBuff`, `persistentReloadBuff`, `heroUpgradeLevel`, `gamePoints`, `powerPoints`, `setPosition(x, y, z)`.

**Методы (25 штук, по группам):**

| Группа | Метод |
|---|---|
| Урон | `takeDamage(srcIndex, damage, ulti, attacker, projectile, hasIndication, hasHighlight, srcX, srcY, someData, forceProtected, origin, forceAll, makeVisible, disallowSpawns, extraValue) -> boolean` |
| Лечение | `takeHeal(srcIndex, damage, hasIndication, someData, origin) -> boolean` |
| Движение | `moveTo(x, y, hasCustomSpeed, customSpeed, isNw, useTeleports)`, `stopMovement()`, `isPlayerControlRemoved()` |
| Скиллы | `getWeaponSkill()`, `getUltiSkill()`, `getSkill(data)`, `useSkill(data, x, y, isAutoAim) -> boolean` |
| Позиция/HP | `increaseMaxHitPoints(value, powerUps)`, `teleport(x, y, srcAreaEffect, destAreaEffect, damage, ultiCharge)` |
| Зоны | `spawnCirclingAreaEffect(damageBonus, data, origin, applyOwnerBuffs, followOwner) -> LogicAreaEffect` |
| Питомцы | `getPet(movingOnly, standingOnly)` |
| Статусы | `addStatusEffect(data, srcIndex, srcTeam, origin, attacker)`, `addStatusEffectSelf(data, origin)`, `blockHealthRegen()` |
| Контроль | `setStun(ticks, skipImmunity, isSleepy, isCrossing)`, `push(pushX, pushY, strength, canFly, a7..a13, skipCCImmunity, useFixedDistance, stunTicks, speedModifier)` |
| Защита/скрытность | `gainShield(ticks, value)` (value = % защиты), `setConsumableShield(value, ticks)`, `setInvisibility(ticks, distanceToSee)` |

> ⚠️ `gainShield` — **сначала тики, потом процент**: `char:gainShield(100, 50)` = 50 % щита на 100 тиков.
> `setConsumableShield` — наоборот: **сначала value, потом тики**.

**Пример «убить наверняка» (приём из TrafficLight.lua и Safe Not Safe):**

```lua
char:takeDamage(
    char.index, 1000000, 0, char, nil,
    true,  false,          -- hasIndication, hasHighlight
    char.x, char.y, nil,
    true,                  -- forceProtected: пробить щит/неуязвимость
    AttackOrigin.UNKNOWN,
    true,                  -- forceAll
    true,                  -- makeVisible
    true,                  -- disallowSpawns
    0
)
```

Два важных нюанса: (1) `forceProtected = true` нужен, иначе временная защита (респавн-щит) отклонит урон; (2) одиночный вызов может не сработать — рабочие скрипты **повторяют** урон, пока персонаж не умрёт (`if not char:isAlive() then ... end`, либо вызов каждый тик по флагу «приговорён»).

### Skill

```lua
local skill = char:getUltiSkill()
if skill then
    skill:setUpgradeLevel(9)              -- уровень улучшения, считается с нуля
    char:useSkill(skill.data, targetX, targetY, true)   -- true = автонаведение
end

local weapon = char:getWeaponSkill()
weapon:charge(50)                          -- +50% патронов (1 = 1/100 патрона), может быть отрицательным
local max = weapon:getMaxCharge()          -- лимит патронов (1000 = 1 полный)
skill:isWeaponSkill() / skill:isUltiSkill()
```

`Skill.data` — это `SkillData`, то есть ровно то, что возвращает `lookup(20, "ИмяСкилла")`. Поэтому оба варианта валидны:

```lua
char:useSkill(lookup(20, "ShotgunGirlUlti"), x, y, false)  -- из библиотеки (Chess/Safe Not Safe)
char:useSkill(char:getUltiSkill().data,     x, y, true)    -- «свой супер» без хардкода имени
```

## 5. lookup() и createObject() — фундамент всего

```lua
local data = lookup(ТИП, "Имя")   -- -> объект данных или nil
local obj  = createObject(data)   -- CharacterData -> LogicCharacter
                                  -- ProjectileData -> LogicProjectile
                                  -- AreaEffectData -> LogicAreaEffect
                                  -- ItemData       -> LogicItem
server.objectManager:addObject(obj)   -- обязательно, иначе объект не появится в бою
```

Полная таблица типов (проверено по `types.d.luau`):

| type | Класс | Что это | Имён |
|---|---|---|---|
| 6 | `ProjectileData` | снаряды | 2074 |
| 15 | `LocationData` | локации | 1357 |
| **16** | `CharacterData` | **персонажи** (`characters.csv`) | 456 |
| 17 | `AreaEffectData` | зоны/эффекты скиллов | 1387 |
| 18 | `ItemData` | предметы (`items.csv`) | 191 |
| 20 | `SkillData` | скиллы (`skills.csv`) | 713 |
| 23 | `CardData` | карты | 1474 |
| **27** | `TileData` | **тайлы/стены** (`tiles.csv`) | 75 |
| 29 | `SkinData` | скины | 1853 |
| 50 | `AccessoryData` | гаджеты | 276 |
| 52 | `EmoteData` | эмоции | 3282 |
| 68 | `SprayData` | спреи | 781 |
| **108** | `TraitData` | **трейты** (`traits.csv`) | 1276 |
| 117 | `StatusEffectData` | статус-эффекты | 455 |

Полные списки имён — в файле [CHEATSHEET_NAMES.md](CHEATSHEET_NAMES.md).

**Готовые спавн-хелперы (практически дословно из Among Us / Chess — их можно копировать в любой свой скрипт):**

```lua
function spawnCharacter(charName, x, y)
    local character = createObject(lookup(16, charName))
    character:setPosition(x, y, 0)
    server.objectManager:addObject(character)
    return character
end

function spawnItem(itemName, x, y)
    local item = createObject(lookup(18, itemName))
    item:setPosition(x, y, 0)
    server.objectManager:addObject(item)
    return item
end

function placeTile(tileName, tileX, tileY, owner)
    if server.map:getTile(tileX, tileY) ~= nil then
        server.map:setDynamicTile(lookup(27, tileName), tileX, tileY, owner)
    end
end
```

### Координаты: мир ↔ тайлы

Проверено по Among Us и Chess — **1 тайл = 300 мировых единиц**, центр тайла = `tile*300 + 150`:

```lua
function subtileToTile(c)  return math.floor(c / 300) end
function tileToSubtile(t)  return t * 300 + 150 end
```

Размер карты: `server.map.tileSizeX / tileSizeY` (в клетках), `server.map.absSizeX / absSizeY` (в единицах; на стандартной карте ≈ 18000, то есть 60×60 тайлов). Рабочий приём из Safe Not Safe — не выходить за карту:

```lua
local margin = 350
local maxX = server.map.absSizeX - margin
local maxY = server.map.absSizeY - margin
x = math.max(margin, math.min(maxX, x))
y = math.max(margin, math.min(maxY, y))
```

## 6. Рецепты

### 6.1 Перебор всех игроков (самый частый паттерн)

```lua
for i = 0, server.playersCount - 1 do
    local p = server:getClientInfo(i)
    if p ~= nil and p.isAlive then
        local char = server.objectManager:getObject(p.objectId)
        if char ~= nil then
            -- работаем с персонажем
        end
    end
end
```

⚠️ `getClientInfo` может вернуть `nil` — проверка обязательна. `p.objectId` бывает `-1` (мёртвый/отсутствует), тогда `getObject` вернёт `nil`.

### 6.2 Перебор всех персонажей в бою (включая ботов, питомцев, турели)

```lua
for _, char in server.objectManager:getCharacters() do
    if char:isAlive() then
        -- char.data:getName() даст имя из characters.csv, например "MechanicTurret"
    end
end
```

Различие важно: вариант 6.1 даёт только игроков, 6.2 — вообще всё живое. Чтобы отсечь лишнее:

```lua
if char.type ~= CharacterType.HERO then return end   -- только бойцы, без турелей/питомцев
```

### 6.3 Трейты — главный инструмент «модов»

```lua
local trait = lookup(108, "Shelly1")     -- трейт = особая способность

char.traits:add(trait)                   -- добавить
char.traits:remove(trait)                -- снять (вернёт boolean)
local t = char.traits:getComponent(TraitType.XXX)  -- проверить наличие по типу
```

Приём «навесить на всех ближников +дальность атаки» из `Add Traits to Brawlers.lua` — ровно 20 строк:

```lua
local traitNames = { "Meg1_Transform", "Meg2_Transform" }
function tick()
    for i = 0, server.playersCount - 1 do
        local p = server:getClientInfo(i)
        if p ~= nil then
            local char = server.objectManager:getObject(p.objectId)
            if char ~= nil then
                for _, name in ipairs(traitNames) do
                    char.traits:add(lookup(108, name))
                end
            end
        end
    end
end
```

⚠️ Трейты в таком цикле навешиваются заново каждый тик. Так работает библиотечный пример, но правильнее — вешать один раз на появление персонажа (см. 6.5). Random Trait.lua прямо предупреждает: спам трейтов **может уронить бой**.

### 6.4 Правильная выдача «один раз на нового персонажа»

Приём из `Projectiles Bounce.lua` — запоминаем последний обработанный id:

```lua
local registered = 0
function tick()
    for _, char in server.objectManager:getCharacters() do
        if char.id > registered then
            char.traits:add(TRAIT_1)
            char.traits:add(TRAIT_2)
            registered = char.id      -- id растут монотонно -> новый персонаж обработан один раз
        end
    end
end
```

Более надёжный вариант — сравнение `objectId` у игрока (приём из TrafficLight) и таблица состояния по индексу:

```lua
local state = {}                        -- state[index] = { character = ..., ... }

for i = 0, server.playersCount - 1 do
    local p = server:getClientInfo(i)
    local s = state[i]
    local char = s and s.character
    if s == nil or char == nil or char.id ~= p.objectId then
        -- игрок зашёл заново или заспавнился заново -> пересоздаём состояние
        local obj = p.objectId >= 0 and server.objectManager:getObject(p.objectId) or nil
        char = (obj ~= nil and obj:getType() == 0) and obj or nil
        state[i] = { character = char }
    end
    state[i].character = char
end
```

Это же решает проблему респавна: после смерти `objectId` меняется, и ты точно знаешь, что надо заново применить трейты/баффы.

### 6.5 Статус-эффекты

```lua
local eff = lookup(117, "GhostIncorporeal")   -- напр. Invulnerable, RollerFire, PuppeteerPoison...

char:addStatusEffectSelf(eff, AttackOrigin.UNKNOWN)          -- «от себя»
char:addStatusEffect(eff, srcIndex, srcTeam, AttackOrigin.MUTATION, attacker)  -- от лица другого

-- у полученного объекта:
eff.ticksLeft, eff.ticksTotal, eff.damageBase, eff.healingBase
eff:addTicks(40)   -- продлить
eff:cancel()       -- снять
eff:isActive()
```

Возвращает `nil`, если эффект уже висит и не является ни `Stackable`, ни `Refreshable` — это не ошибка, просто проверяй на `nil`.

### 6.6 Телепорт, стан, отталкивание, щит, невидимость

```lua
char:teleport(x, y, nil, nil, 0, 0)          -- + эффекты в точке выхода/входа, урон, заряд супера
char:setStun(40, false, false, false)        -- 40 тиков (2 сек) стана
char:push(char.x - 300, char.y, 1.0, false, false,false,false, false, false,false,false, false, 0, 1.0)
char:gainShield(80, 50)                      -- 50% щита на 4 секунды
char:setConsumableShield(2000, 100)          -- 2000 HP «банки» на 5 секунд
char:setInvisibility(200, -1)                -- 10 сек невидимости, -1 = не раскрывать по дистанции
```

Из Among Us: `setInvisibility(10000000, -1)` — «навсегда скрыть» (например, выброшенного игрока), `setInvisibility(2, -1)` — мигнуть на 0.1 сек.

### 6.7 Работа с картой

```lua
local tile = server.map:getTile(tx, ty)           -- nil, если вне карты
tile.data, tile.dataOriginal, tile.x, tile.y
tile:isDynamic()                                  -- поставлен скриптом?
tile:restoreOriginal()                            -- вернуть как было в начале боя

server.map:destructTile(tx, ty, true)             -- снести блок (true = обычная атака)
server.map:setDynamicTile(lookup(27, "Wall1"), tx, ty, char)  -- поставить блок
```

`dynamicCode` из Among Us — это просто имя из `tiles.csv`. Все 75 имён (Wall1, Wall2, Crate, Bouncer, Teleport1–4, Healing, Slow, Fast, SpringBoard, Forest, Water, …) — в шпаргалке.

### 6.8 Предметы и спреи

```lua
local spray = createObject(lookup(18, "Spray"))
spray:setIndex(char.index, char.team)   -- «привязать» к игроку
spray.sprayDataIndex = 5                -- номер спрея
spray:setPosition(char.x, char.y, 0)
server.objectManager:addObject(spray)
-- позже: spray:destroy()
```

Приём из TrafficLight: спрей переставляется за персонажем каждый тик, а при смене индекса старый уничтожается и создаётся новый. Это дешёвый способ рисовать «индикатор состояния» у каждого игрока (красный/зелёный светофор).

### 6.9 Зоны (AreaEffect)

```lua
-- привязанная к персонажу зона (супер Эмз, лечение Пэм, зарядка Базза):
local zone = char:spawnCirclingAreaEffect(0, lookup(17, "MegaBossWarning360"),
                                          AttackOrigin.UNKNOWN, false, false)
zone:setPosition(char.x, char.y, 0)

-- самостоятельная зона:
local z = createObject(lookup(17, "SomeArea"))
z:setSource(char.index, char.team, char, AttackOrigin.MUTATION)
z:setPosition(x, y, 0)
server.objectManager:addObject(z)
z:trigger()                    -- ОБЯЗАТЕЛЬНО один раз после addObject, иначе не сработает
z.damage = 1000                -- урон зоны
z.ultiEnergy = 0               -- сколько ульты заряжает каждое попадание
z:isObjectInside(otherObj)     -- проверка попадания
z:destroy()
```

### 6.10 Снаряды

```lua
for _, proj in server.objectManager:getProjectiles() do
    proj.finishState   -- 0 = летит, 1 = макс. дистанция, 2 = граница карты,
                       -- 3 = попадание в персонажа, 4 = попадание в блок, 5 = уничтожен
    proj.shotCharacter -- в кого попал (или nil)
    proj.origin        -- AttackOrigin
    proj.data:getName() -- напр. "ShotgunGirlProjectile"
end
```

**Предсказание траектории (приём из Safe Not Safe):** хранить позиции снаряда из прошлого тика и считать вектор:

```lua
local prev = projHistory[proj.id]
if prev then
    local vx, vy = proj.x - prev.x, proj.y - prev.y
    local speed = math.sqrt(vx*vx + vy*vy)
    if speed > 10 then
        local dx, dy = vx/speed, vy/speed          -- единичный вектор полёта
        -- направление «на меня»: (safe.x - proj.x, safe.y - proj.y)
        -- скалярное произведение < 0 => снаряд летит в мою сторону
    end
end
```

Так же детектится попадание твоего снаряда в конкретного врага (`finishState == 3 and shotCharacter`), что использовано для «ульта Шелли ваншотит того, в кого попала».

### 6.11 Подписки на события (есть в типах и reference)

`LogicCharacter` объявляет 5 списков подписок: `takingDamageListeners`, `dealingDamageListeners`, `deathListeners`, `skillUseListeners`, `startOverchargeListeners`. Обработчики создаются через `createCallback`:

```lua
char.takingDamageListeners:add(createCallback("DamageEventListener",
    function(source, projectile, damage, data, origin)
        log(char.data:getName() .. " получил " .. damage)
    end))

char.deathListeners:add(createCallback("SourceListener",
    function(origin) log("персонаж погиб") end))
```

Сигнатуры (`types.d.luau`):

```lua
DamageEventListener = (source, projectile, damage, data, origin) -> ()
SkillEventListener  = (skill) -> ()
SourceListener      = (origin) -> ()
BasicListener       = () -> ()
```

Честная оговорка: **в библиотеке из SCRIPTS-INFO ни один скрипт подписки не использует** — все 8 работ построены на опросе состояния в `tick()`. Подписки описаны в официальной документации и в типах, но живых примеров нет, поэтому проверяй их на практике; опрос в `tick()` — гарантированно рабочий путь.

### 6.12 Чат, цвет, JSON

```lua
log("текст в чат")
log(colorText("GREEN LIGHT", "00ff00"))       -- хелпер из Among Us: colorText(str, hex)
log("<cff0000>RED LIGHT</c>")                 -- вариант разметки из TrafficLight
local s = json.encode({ a = 1 })              -- json.encode / json.decode
```

## 7. Разбор скриптов библиотеки — какие приёмы там лежат

| Скрипт | Что демонстрирует | Приёмы, которые стоит забрать |
|---|---|---|
| **Add Traits to Brawlers.lua** (20 строк) | Минимальный рабочий скрипт | `hasIntroSkip`, цикл по игрокам, `traits:add(lookup(108, имя))` |
| **Projectiles Bounce.lua** (15 строк) | Все пули отскакивают как у Рико | Защита «один раз на персонажа» через `char.id > registered` |
| **Supers shoot 360.lua** (23 строки) | Суперы летят на 360° | Принудительная зарядка: `p.ultiCharge = p.maxUltiCharge`, `p.overchargeCharge = p.maxOverchargeCharge` — до зарядки `lookup`, т.к. `p` может быть `nil` |
| **Random Trait.lua** (37 КБ) | Случайные трейты каждые 3 сек | Проверка респавна через `wasAlive[index]`; **детектор краша** — если игрок не двигался N тиков, скрипт пишет в лог и глушит себя (`crashDetected`); `debugFinishBattle` |
| **Traffic Light.lua** (16 КБ, собран NB Tools) | «Кальмар»: движение на красный = смерть | Модульная архитектура (config/phases/signals/movement/damage/players/main); фиксация позы (`x,y,z,angleHead,angleLegs`) и детект отклонения с допуском; разница углов через `math.abs((cur - prev + 180) % 360 - 180)`; спавн спрея-индикатора с уничтожением старого; `server:getRandomInt(min, max+1)` (правая граница исключается!) |
| **Safe Not Safe.lua** (43 КБ) | Бот-«сейф», который уворачивается от атак, прыгает, крутится и убивает ультой Шелли | Захват персонажа-цели по имени (`char.data:getName()`); предсказание снарядов по вектору; оценка безопасной стороны уклонения (`evaluateDodgeSide` + `isPointInHazard`); движение прямой записью `setPosition` + `clampToMap`; ломание стен вокруг себя (`destructTile` в радиусе); ваншот по попавшим (`finishState == 3` + `shotCharacter`); **всё опасное обёрнуто в `pcall`** |
| **Among Us v1.5.4** (77 КБ) | Полная игра на кастомной карте | Спавн персонажей/предметов/тайлов; телепорт и «прятки» на интро; скрытие тел (`setInvisibility(10000000, -1)` + `GhostIncorporeal` + `DeadMariachiBuddySp2Silence`); «кнопка» через эмодзи (`emoteUsedTick + 1 == server.tick`); `getNearestBody`, подсчёт живых, `debugFinishBattle`; кастомный `colorText`; очистка предметов в конце тика |
| **Chess.lua** (57 КБ) | Полностью рабочие шахматы | **Ввод игрока выстрелом**: `getProjectiles()` → `proj.index` (кто стрелял) + `proj.x/proj.y` (куда) = «клик по клетке»; подсветка возможных ходов предметами (`ConductorSign`) и их очистка; ступенчатые задания с бюджетом на тик (`stepSetupChessField`, `stepEvaluateGameState`, `stepSpawnMoveMarkers`); `checkStuckMoves` — если фигура «застряла» (стан/снаряд), её телепортируют в целевую клетку; `moveTo(destX, destY, true, 1000, false, false)` — движение с кастомной скоростью |

Самые ценные идеи, которые я бы вынес отдельно:

1. **Ввод игрока без UI.** Отдельного API для кнопок нет. Работают два канала: (а) выстрел игрока — читаешь `proj.index`/`proj.x`/`proj.y` и трактуешь как клик (Chess); (б) эмодзи/пин — `emoteUsedTick + 1 == server.tick` (Chess, Among Us). Всё остальное — движение и позиции.
2. **`forceProtected = true` + повтор урона.** Один вызов `takeDamage` не гарантирует смерть.
3. **Движение можно писать напрямую** `setPosition` каждый тик (Safe Not Safe), а можно через `moveTo` (Chess) — первый вариант даёт полный контроль траектории, второй — честный путь с обходом препятствий.
4. **Дорогое — в кэш.** `lookup()` и `createObject()` в цикле на 60 персонажей каждый тик = лаги. lookup наверху, объекты — один раз.
5. **`pcall` вокруг всего потенциально падающего** — стандарт в Safe Not Safe.

## 8. Архитектура и производительность

**Модульный стиль (как TrafficLight.lua)** — если скрипт больше ~150 строк, разбивай логически:

```lua
local Config   = { ... }        -- все числа/имена вверху
local State    = { ... }        -- состояние игроков
local Phases   = { ... }        -- логика фаз/режимов
local Players  = { ... }        -- работа с игроками
local Signals  = { ... }        -- визуал (спреи/зоны)
local Damage   = { ... }        -- урон/смерть

function tick()
    local now = server.tick
    local changed = Phases.update(now)
    Players.update(changed)
end
```

**Правила производительности:**

| Нельзя | Надо |
|---|---|
| `lookup()` внутри цикла по игрокам каждый тик | `lookup()` один раз на этапе загрузки |
| Спавнить объект каждый тик | Помечать по `char.id` / `objectId`, спавнить при изменении |
| Один огромный скан в одном тике | Разбить на порции (бюджет N итераций на тик) |
| `getCharacters()` несколько раз за тик | Один раз в локальную переменную |
| Логировать каждый тик | Логировать по событию или раз в N тиков |
| Плодить трейты (Random Trait) | Даёт нестабильность и вылеты — только по необходимости и с проверкой `getComponent` |

## 9. Подводные камни

1. **Игровая логика перезаписывает движение.** Если персонаж «идёт» по своему пути, твои координаты затрутся. Для полного контроля — `stopMovement()` или запись `setPosition` каждый тик.
2. **Клиентские поля обновляются в конце тика.** `p.x`, `p.isAlive`, `char.hitPoints` — значения «на начало тика».
3. **`getRandomInt(N, M)` не включает M.** Для диапазона 10–15 пиши `getRandomInt(10, 16)`. В TrafficLight это прямо помечено комментарием — частая ошибка.
4. **Порядок аргументов у похожих методов различается**: `gainShield(ticks, value)`, но `setConsumableShield(value, ticks)`, а у `teleport` сначала координаты, потом два `AreaEffectData`, потом урон и заряд.
5. **`setDynamicTile` требует `DynamicCode != 0`** у тайла — «Open»/«Empty» не выставятся.
6. **`addObject` без `trigger()` для зоны — молча не работает** (для `LogicAreaEffect`).
7. **`p.objectId` может быть `-1`** — `getObject(-1)` вернёт `nil`, проверяй.
8. **`getType()` требует числа, а не класса**: `obj:getType() == 0` (персонаж). Сравнение с `CharacterType.HERO` — это уже поле `char.type` у персонажа.
9. **Углы — градусы 0..360**, и сравнивать их надо через разность по кругу: `math.abs((cur - prev + 180) % 360 - 180)`.
10. **Различие `team` и `getAttackTeam()`** — если в бою есть Виллоу, обычное `team` даст неверный результат.
11. **Тяжёлые скрипты стабильнее, когда сами себя выключают.** В Random Trait это буквально: детект зависания → `log` → остановка логики. Делай так же, если скрипт может уронить бой.
12. **`server.hasIntroSkip` / `hasPoisonDisabled`** ставятся на этапе загрузки — в `tick()` их менять поздно.

## 10. Чек-лист отладки

- [ ] `server.hasIntroSkip = true` стоит — иначе логика выполняется во время интро и ломается.
- [ ] В начале `tick()` есть `if server.isBattleEnded then return end`.
- [ ] `getClientInfo` проверяется на `nil`.
- [ ] `lookup(...)` проверяется на `nil` (опечатка в имени = `nil` = ошибка в рантайме).
- [ ] Все `lookup()` вынесены из `tick()` в загрузку.
- [ ] Для спавнов есть защита от повторов (по `id`/`objectId`/флагу).
- [ ] Урон наносится с `forceProtected = true`, повторяется, если цели не умер.
- [ ] Тяжёлые циклы разбиты по тикам.
- [ ] Потенциально падающие куски в `pcall`.
- [ ] Логи не спамят каждый тик.
- [ ] Одиночные тесты логикой: один игрок, один бот, проверка в пустом бою.

## 11. Что я сделал по итогу

Рядом лежат 4 скрипта, которые я написал сам по этому API — они же служат примерами стиля:

| Файл | Что делает | Какие механики показывает |
|---|---|---|
| [examples/01_autoaim_super.lua](examples/01_autoaim_super.lua) | Авто-наведение супера в ближайшего врага + автозаряд | `getClientInfo`, `getUltiSkill().data`, `useSkill`, `ultiCharge`, поиск ближайшего врага, `getAttackTeam` |
| [examples/02_damage_events.lua](examples/02_damage_events.lua) | Логирование урона/смертей, лаифстил, авто-щит при низком HP | подписки `takingDamageListeners` / `deathListeners` + `createCallback`, `takeHeal`, `gainShield`, `colorText` |
| [examples/03_map_control.lua](examples/03_map_control.lua) | Арена «наоборот»: расставить стены, зона урона, телепорт-ловушки | `setDynamicTile`, `destructTile`, `restoreOriginal`, `getTile`, конвертация координат, `createObject` зоны + `trigger`, `teleport` |
| [examples/04_hunter_bots.lua](examples/04_hunter_bots.lua) | Боты охотятся: идут к врагу и стреляют, стан в упор | `moveTo` с кастомной скоростью, `stopMovement`, `getWeaponSkill`, `setStun`, `push`, состояние по `objectId` |

Идентификаторы имён для всех скриптов — в [CHEATSHEET_NAMES.md](CHEATSHEET_NAMES.md) (персонажи, тайлы, трейты, статусы, скиллы, зоны, снаряды, гаджеты, спреи + соответствие «кодовое имя → бойец»).

Исходники, из которых я это собрал, лежат в `repo/` (`repo/csv/`, `repo/scripts/`, `repo/docs/`) — можно перепроверить любую строку.
