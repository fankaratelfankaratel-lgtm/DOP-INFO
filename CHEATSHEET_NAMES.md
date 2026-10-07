# Шпаргалка имён для `lookup()` — Brawl Stars / NB Scripting

Источники: [types.d.luau](https://github.com/segnpa66-lab/nb-scripts-authors/blob/a5e4e428bbc8739eb14380b610be99b01448c2ce/nb-scripting%2Ftypes.d.luau), [CSV-репозиторий](https://github.com/fankaratelfankaratel-lgtm/-CSV-/tree/main), [официальная документация](https://github.com/nulls-mods-community/scripting-docs/blob/main/reference.md)

## 1. Таблица типов для `lookup(type, name)`

Вызов: `lookup(ТИП, "Имя")` → объект данных (`ProjectileData`, `CharacterData`, …) или `nil`, если имя неверное.

| type | Класс данных | Что это | Всего имён | Читаемых имён |
|---|---|---|---|---|
| `6` | ProjectileData | снаряды (projectiles) | 2074 | 2070 |
| `15` | LocationData | локации | 1357 | 1357 |
| `16` | CharacterData | персонажи (characters.csv) | 456 | 450 |
| `17` | AreaEffectData | зоны/скиллы (area_effects) | 1387 | 1386 |
| `18` | ItemData | предметы (items.csv) | 191 | 190 |
| `20` | SkillData | скиллы (skills.csv) | 713 | 709 |
| `23` | CardData | карты | 1474 | 1461 |
| `27` | TileData | тайлы/стены (tiles.csv) | 75 | 75 |
| `29` | SkinData | скины | 1853 | 1834 |
| `50` | AccessoryData | гаджеты/аксессуары | 276 | 275 |
| `52` | EmoteData | эмоции | 3282 | 3275 |
| `68` | SprayData | спреи | 781 | 780 |
| `108` | TraitData | трейты (traits.csv) | 1276 | 1276 |
| `117` | StatusEffectData | статус-эффекты | 455 | 455 |

Важно: тип и имя чувствительны к регистру. Часть «имён» — это хеши (32-hex) из внутренних таблиц; они тоже рабочие, но непонятны человеку.

## 2. Персонажи: кодовое имя ↔ игровое (`lookup(16, ...)`)

`ItemName` — внутреннее имя бойца, `WeaponSkill` / `UltimateSkill` — его скиллы (для `lookup(20, ...)`).

> Здесь только **бойцы** (тип `Hero`, 122 шт.). Роботы, боссы, турели и петы (313 объектов) — в разделе **11**, включая медведя Ниты, турель Джесси и артиллерию Пенни.

| Кодовое имя в игре (`Name`) | ItemName | WeaponSkill | UltimateSkill |
|---|---|---|---|
| `ShotgunGirl` | shelly | `ShotgunGirlWeapon` | `ShotgunGirlUlti` |
| `Gunslinger` | colt | `GunslingerWeapon` | `GunslingerUlti` |
| `BullDude` | bull | `BullDudeWeapon` | `BullDudeUlti` |
| `RocketGirl` | brock | `RocketGirlWeapon` | `RocketGirlUlti` |
| `TrickshotDude` | ricochet | `TrickshotDudeWeapon` | `TrickshotDudeUlti` |
| `Cactus` | spike | `CactusWeapon` | `CactusUlti` |
| `Barkeep` | barley | `BarkeepWeapon` | `BarkeepUlti` |
| `Mechanic` | jessie | `MechanicWeapon` | `MechanicUlti` |
| `Shaman` | nita | `ShamanWeapon` | `ShamanUlti` |
| `TntDude` | dynamike | `TntDudeWeapon` | `TntDudeUlti` |
| `Luchador` | elprimo | `LuchadorWeapon` | `LuchadorUlti` |
| `Undertaker` | mortis | `UndertakerWeapon` | `UndertakerUlti` |
| `Crow` | crow | `CrowWeapon` | `CrowUlti` |
| `DeadMariachi` | poco | `DeadMariachiWeapon` | `DeadMariachiUlti` |
| `BowDude` | bo | `BowDudeWeapon` | `BowDudeUlti` |
| `Sniper` | piper | `SniperWeapon` | `SniperUlti` |
| `MinigunDude` | pam | `MinigunDudeWeapon` | `MinigunDudeUlti` |
| `BlackHole` | tara | `BlackHoleWeapon` | `BlackHoleUlti` |
| `BarrelBot` | darryl | `BarrelBotWeapon` | `BarrelBotUlti` |
| `ArtilleryDude` | penny | `ArtilleryDudeWeapon` | `ArtilleryDudeUlti` |
| `HammerDude` | frank | `HammerDudeWeapon` | `HammerDudeUlti` |
| `HookDude` | gene | `HookWeapon` | `HookUlti` |
| `ClusterBombDude` | tick | `ClusterBombDudeWeapon` | `ClusterBombDudeUlti` |
| `Ninja` | leon | `NinjaWeapon` | `NinjaUlti` |
| `Rosa` | rosa | `RosaWeapon` | `RosaUlti` |
| `Whirlwind` | carl | `WhirlwindWeapon` | `WhirlwindUlti` |
| `Baseball` | bibi | `BaseballWeapon` | `BaseballUlti` |
| `Arcade` | 8bit | `ArcadeWeapon` | `ArcadeUlti` |
| `Sandstorm` | sandy | `SandstormWeapon` | `SandstormUlti` |
| `BeeSniper` | bea | `BeeSniperWeapon` | `BeeSniperUlti` |
| `Mummy` | emz | `MummyWeapon` | `MummyUlti` |
| `SpawnerDude` | mr.p | `SpawnerDudeWeapon` | `SpawnerDudeUlti` |
| `Speedy` | max | `SpeedyWeapon` | `SpeedyUlti` |
| `07220d24fa2e06c356cad4e7c6037d70b265010e` | shelly | `ShotgunGirlWeapon` | `ShotgunGirlUlti` |
| `Driller` | jacky | `DrillerWeapon` | `DrillerUlti` |
| `Blower` | gale | `BlowerWeapon` | `BlowerUlti` |
| `Controller` | nani | `ControllerWeapon` | `ControllerUlti` |
| `Wally` | sprout | `WallyWeapon` | `WallyUlti` |
| `PowerLeveler` | surge | `PowerLevelerWeapon` | `PowerLevelerUlti` |
| `Percenter` | colette | `PercenterWeapon` | `PercenterUlti` |
| `FireDude` | amber | `FireDudeWeapon` | `FireDudeUlti` |
| `IceDude` | lou | `IceDudeWeapon` | `IceDudeUlti` |
| `SnakeOil` | byron | `SnakeOilWeapon` | `SnakeOilUlti` |
| `Enrager` | edgar | `EnragerWeapon` | `EnragerUlti` |
| `Ruffs` | ruffs | `RuffsWeapon` | `RuffsUlti` |
| `Roller` | stu | `RollerWeapon` | `RollerUlti` |
| `ElectroSniper` | belle | `ElectroSniperWeapon` | `ElectroSniperUlti` |
| `StickyBomb` | squeak | `StickyBombWeapon` | `StickyBombUlti` |
| `CrossBomber` | grom | `CrossBomberWeapon` | `CrossBomberUlti` |
| `RopeDude` | buzz | `RopeDudeWeapon` | `RopeDudeUlti` |
| `AssaultShotgun` | griff | `AssaultShotgunWeapon` | `AssaultShotgunUlti` |
| `Knight` | ash | `KnightWeapon` | `KnightUlti` |
| `MechaDude` | meg | `MechaDudeWeapon` | `MechaDudeUlti` |
| `Duplicator` | lolla | `DuplicatorWeapon` | `DuplicatorUlti` |
| `KickerDude` | fang | `KickerDudeWeapon` | `KickerDudeUlti` |
| `4f7b8a8fb970bd4cb356d59fd76bb5fb64e5797a` | shelly | `ShotgunGirlWeapon` | `ShotgunGirlUlti` |
| `Flea` | eve | `FleaWeapon` | `FleaUlti` |
| `JetpackGirl` | janet | `JetpackGirlWeapon` | `JetpackGirlUlti` |
| `CannonGirl` | bonnie | `CannonGirlWeapon` | `CannonGirlUlti` |
| `Silencer` | otis | `SilencerWeapon` | `SilencerUlti` |
| `WeaponThrower` | sam | `WeaponThrowerWeapon` | `WeaponThrowerUlti` |
| `SoulCollector` | gus | `SoulCollectorWeapon` | `SoulCollectorUlti` |
| `ShieldTank` | buster | `ShieldTankWeapon` | `ShieldTankUlti` |
| `Jester` | chester | `JesterWeapon` | `JesterUltiExploding` |
| `DoorMan` | gray | `DoorManWeapon` | `DoorManUlti` |
| `Beamer` | mandy | `BeamerWeapon` | `BeamerUlti` |
| `Splitter` | artie | `SplitterWeapon` | `SplitterUlti` |
| `Puppeteer` | willow | `PuppeteerWeapon` | `PuppeteerUlti` |
| `Maisie` | maisie | `MaisieWeapon` | `MaisieUlti` |
| `FishTank` | fishtank | `FishTankWeapon` | `FishTankUlti` |
| `Duelist` | cordelius | `DuelistWeapon` | `DuelistUlti` |
| `Reviver` | doug | `ReviverWeapon` | `ReviverUlti` |
| `Cooker` | pearl | `CookerWeapon` | `CookerUlti` |
| `Conductor` | chuck | `ConductorWeapon` | `ConductorUltiSpawn` |
| `Cocooner` | charlie | `CocoonerWeapon` | `CocoonerUlti` |
| `Leaper` | mico | `LeaperWeapon` | `LeaperUlti` |
| `Attacher` | kit | `AttacherWeapon` | `AttacherUlti` |
| `Twins` | twins | `TwinsWeaponThrower` | `TwinsUlti` |
| `AxeJuggler` | melody | `AxeJugglerWeapon` | `AxeJugglerUlti` |
| `InsectMan` | angelo | `InsectManWeapon` | `InsectManUlti` |
| `DragonRider` | draco | `DragonRiderWeapon` | `DragonRiderUlti` |
| `Ambusher` | lily | `AmbusherWeapon` | `AmbusherUlti` |
| `Painter` | berry | `PainterWeapon` | `PainterUlti` |
| `Crab` | clancy | `CrabWeapon1` | `CrabUlti1` |
| `Digger` | digger | `DiggerWeapon` | `DiggerUlti` |
| `Samurai` | samurai | `SamuraiWeaponDash` | `SamuraiUlti` |
| `Ghost` | shade | `GhostWeapon` | `GhostUlti` |
| `Voodoo` | juju | `VoodooWeaponEarth` | `VoodooUlti` |
| `Lightyear` | lightyear | `LightyearWeapon` | `LightyearUlti` |
| `Meeple` | meeple | `MeepleWeapon` | `MeepleUlti` |
| `Skater` | ollie | `SkaterWeapon` | `SkaterUlti` |
| `Morningstar` | lumi | `MorningstarWeapon` | `MorningstarUlti` |
| `Chronomancer` | finx | `ChronomancerWeapon` | `ChronomancerUlti` |
| `Alternator` | jae | `AlternatorWeaponSpeed` | `AlternatorUltiHeal` |
| `Geisha` | kaze | `GeishaWeapon` | `GeishaUlti` |
| `Stalker` | alli | `StalkerWeaponDash` | `StalkerUlti` |
| `Domain` | trunk | `DomainWeapon` | `DomainUlti` |
| `Dancer` | dancer | `DancerWeaponSingle` | `DancerUlti` |
| `Fury` | fury | `FuryWeapon` | `FuryUlti` |
| `Bulletstorm` | pierce | `BulletstormWeapon` | `BulletstormUlti` |
| `Daredevil` | gigi | `DaredevilWeapon` | `DaredevilUlti` |
| `Mender` | mender | `MenderWeapon` | `MenderUlti` |
| `Shadowdemon` | shadowdemon | `ShadowdemonWeapon` | `ShadowdemonUltiCommand` |
| `Redirecter` | redirecter | `RedirecterWeapon` | `RedirecterUlti` |
| `Gladiator` | gladiator | `GladiatorWeapon` | `GladiatorUltiArena` |
| `MagicalGirl` | stella | `MagicalGirlWeapon` | `MagicalGirlUlti` |
| `Rock` | bolt | `RockWeapon` | `RockUlti` |
| `KatanaKid` | katanakid | `KatanaKidWeaponSlash` | `KatanaKidUlti` |
| `FutureGirl` | wendy | `FutureGirlWeapon` | `FutureGirlUlti` |
| `49c039b18c82880638cd3ba472dc5db3e8cc6f8b` | shelly | `ShotgunGirlWeapon` | `ShotgunGirlUlti` |
| `4028aae4a6bbbdea17608222005fefc028ff7c45` | shelly | `ShotgunGirlWeapon` | `ShotgunGirlUlti` |
| `037424c2385e031824f496c787e2ab8f473b70f8` | shelly | `ShotgunGirlWeapon` | `ShotgunGirlUlti` |
| `f12191a373cbc743d1f7554b27999006a017d2eb` | shelly | `ShotgunGirlWeapon` | `ShotgunGirlUlti` |

Полный список типов персонажей и питомцев (тип 16, читаемые имена):

`AirDisc`, `Alternator`, `Ambusher`, `AngelicPet`, `AngelicPetBig`, `AngelicPetSiege`, `Arcade`, `ArcadeBuddy`
`ArenaBase`, `ArenaBig`, `ArenaMelee`, `ArenaRange`, `ArenaSmall`, `ArenaSpecialMelee`, `ArenaTower`, `ArenaTowerDestroyed`
`ArtilleryDude`, `ArtilleryDudeCover`, `ArtilleryDudeTurret`, `AssaultShotgun`, `AssaultShotgunBombBuddy`, `AssaultShotgunBuddy`, `Attacher`, `Attractor`
`AxeJuggler`, `Barkeep`, `BarrelBot`, `Baseball`, `BaseballBuddy`, `BasketBall`, `Beamer`, `Bee`
`BeeSniper`, `BeeSniperSlowPot`, `BlackHole`, `BlackHolePet`, `BlackHolePet2`, `BlackHolePetGadget`, `Blower`, `BoneThrowerPet`
`BossBot`, `BossMinionST`, `BossRaceBoss`, `Boulder`, `BowDude`, `BowDudeBuddy`, `BowDudeTotem`, `BowDudeTotemBuddy`
`BoxBomb`, `BullBuddy`, `BullDude`, `Bulletstorm`, `Cactus`, `CactusBuddy`, `CactusCover`, `CactusCoverBuddy`
`CactusCoverNanoFake`, `CannonGirl`, `CannonGirlSmall`, `CaptureFlag`, `ChargeBall`, `ChargePuck`, `Chronomancer`, `ClusterBombDude`
`ClusterBombPet`, `Cocooner`, `CocoonerCocoon`, `CocoonerPet`, `Conductor`, `ConductorBuddy`, `Controller`, `ControllerAddon`
`Cooker`, `CoopBoss1`, `CoopBoss2`, `CoopBoss3`, `CoopFastMeleeEnemy1`, `CoopFastMeleeEnemy2`, `CoopFastMeleeEnemy3`, `CoopFastMeleeEnemy4`
`CoopMeleeEnemy1`, `CoopMeleeEnemy2`, `CoopMeleeEnemy3`, `CoopMeleeEnemy4`, `CoopRangedEnemy1`, `CoopRangedEnemy2`, `CoopRangedEnemy3`, `CoopRangedEnemy4`
`Crab`, `CrossBomber`, `CrossBomberVisionTower`, `Crow`, `CrowBuddy`, `DamageBooster`, `DamageBoosterOvercharge`, `Dancer`
`DancerFairy`, `Daredevil`, `DeadMariachi`, `DeadMariachiBuddy`, `DemonicPet`, `DemonicPetSiege`, `Digger`, `DiggerDrill`
`DodgeBall`, `Domain`, `DoorMan`, `DragonRider`, `Driller`, `Duelist`, `Duplicator`, `DuplicatorPet`
`ElectroSniper`, `Enrager`, `EnragerBuddy`, `EventModifierBoss`, `ExplodingBarrel`, `ExplodingTank`, `ExtractionFastMeleeEnemy`, `ExtractionMeleeEnemy`
`ExtractionRangedEnemy`, `FireDude`, `FireDudeBarrel`, `FireDudeBuddy`, `FishTank`, `Flea`, `FleaBigEgg`, `FleaExtraPet`
`FleaHealingPet`, `FleaOverchargedBigEgg`, `FleaPet`, `Fury`, `FutureGirl`, `FutureGirlTurret`, `Geisha`, `GeishaTransformed`
`Ghost`, `GhostBuddy`, `Gladiator`, `Goalkeeper`, `Godzilla`, `Gunslinger`, `GunslingerBuddy`, `HammerDude`
`HammerDudeBuddy`, `HealingStation`, `HeistBomb`, `HighlightEnvironment`, `HockeyGoalkeeper`, `HoldingBall`, `HookDude`, `IceDude`
`InsectMan`, `InvasionBossEnemy`, `InvasionFastMeleeEnemy`, `InvasionMeleeEnemy`, `InvasionRangedEnemy`, `Jester`, `JetpackGirl`, `JetpackGirlDamageTower`
`KatanaKid`, `KickerDude`, `Knight`, `KnightPet`, `LaserBall`, `LastStandMinion`, `Leaper`, `Lightyear`
`LightyearFlight`, `LightyearSword`, `LootBox`, `LoveBomb`, `Luchador`, `LuchadorBuddy`, `MagicalGirl`, `MagicalGirlFlyArea`
`Maisie`, `MechaDude`, `MechaDudeAddon`, `MechaDudeBig`, `MechaDudeBuddy`, `MechaDudeReloadTower`, `MechaVanBossMeleeNinja`, `MechaVanBossSniper`
`MechaVanBossTank`, `MechaVanCart`, `MechaVanFodderBomb`, `MechaVanFodderMelee`, `MechaVanFodderRanged`, `MechaVanFriendlyMegBoss`, `MechaVanMiniMeleeNinja`, `MechaVanMiniSniper`
`MechaVanMiniTank`, `Mechanic`, `MechanicTurret`, `Meeple`, `MegaBossBearWithNitaCustom`, `MegaBossBlackHoleExplodePet`, `MegaBossBlackHoleShieldPet`, `MegaBossBlackhole`
`MegaBossCactusCover`, `MegaBossChronomancerL1`, `MegaBossChronomancerL2`, `MegaBossClusterBomb`, `MegaBossClusterBombPetBig`, `MegaBossClusterBombPetMid`, `MegaBossClusterBombPetSmall`, `MegaBossCrow`
`MegaBossCrowDragonL1`, `MegaBossCrowDragonL2`, `MegaBossCrowDragonL3`, `MegaBossCrowDragonL3Ghost1`, `MegaBossCrowRed`, `MegaBossCrowWhite`, `MegaBossDuo`, `MegaBossDuo20P`
`MegaBossDuo5P`, `MegaBossDuoAngry`, `MegaBossDuoAngry20P`, `MegaBossDuoAngry5P`, `MegaBossEmz`, `MegaBossFang`, `MegaBossFinxKitten`, `MegaBossFixStasisTower`
`MegaBossFixStasisTowerSecond`, `MegaBossFrank`, `MegaBossGhost`, `MegaBossGriff`, `MegaBossGrom`, `MegaBossGromRatPet`, `MegaBossInsectMan`, `MegaBossKatanaKid`
`MegaBossKatanaKid_FishSpawner1`, `MegaBossKatanaKid_FishSpawner2`, `MegaBossKenji`, `MegaBossKenjiGhost`, `MegaBossMaisie`, `MegaBossMaisieTurret`, `MegaBossNitaWithBearCustom`, `MegaBossPercenter`
`MegaBossPercenterPet`, `MegaBossPercenterTurret`, `MegaBossRocketGirlL1`, `MegaBossRocketGirlL2`, `MegaBossRocketGirlL3`, `MegaBossSTDg`, `MegaBossSTVec`, `MegaBossShamanPet`
`MegaBossSpike`, `MegaBossSplitter`, `MegaBossSplitterHead`, `MegaBossStickyBomb`, `MegaBossTrickshot`, `MegaBossTrickshotBrawlentines`, `MegaBossTrickshotBrawlentines2`, `MegaBossTrickshotBrawlentines3`
`MegaFrankMeleeEnemy`, `MegaKenjiPet`, `MegaSamuraiMeleeEnemy`, `MegaSamuraiRangedEnemy`, `MegaSplitterTwinsEnemyShoot`, `MegaSplitterTwinsEnemyThrow`, `MeleeBot`, `MeleeFastBot`
`Mender`, `MineCart0`, `MineCart1`, `MineCart2`, `MineCart3`, `MineCart4`, `MinigunDude`, `Morningstar`
`MultiLaserBall`, `Mummy`, `MummyBuddy`, `NanoDeliveryBot`, `NanoGuardBomb`, `NanoGuardFodderMelee`, `NanoGuardFodderRanged`, `NanoGuardMelee`
`NanoGuardRanged`, `NanoGuardTank`, `NanoIngredient0`, `NanoIngredient1`, `NanoIngredient10`, `NanoIngredient11`, `NanoIngredient12`, `NanoIngredient13`
`NanoIngredient14`, `NanoIngredient15`, `NanoIngredient16`, `NanoIngredient17`, `NanoIngredient18`, `NanoIngredient19`, `NanoIngredient2`, `NanoIngredient3`
`NanoIngredient4`, `NanoIngredient5`, `NanoIngredient6`, `NanoIngredient7`, `NanoIngredient8`, `NanoIngredient9`, `Ninja`, `NinjaBuddy`
`NinjaFake`, `NinjaInvisibleArea`, `NinjaInvisibleAreaBuddy`, `NinjaMutation`, `NinjaNanoPowerClone`, `OverchargedDuplicatorPet`, `OverchargedFutureGirlTurret`, `OverchargedHealingStation`
`OverchargedRedirecterSnakePet`, `OverchargedSpawnerDudeTurret`, `OverchargedSpawnerPet`, `PaintBall`, `Painter`, `Payload`, `PayloadSingle`, `Percenter`
`PercenterBuddy`, `PercenterPet`, `PoisonBarrel`, `PowerLeveler`, `PowerLevelerBuddy`, `Puppeteer`, `RaidBoss`, `RaidBossFastMeleeEnemy1`
`RaidBossFastMeleeEnemy2`, `RaidBossFastMeleeEnemy3`, `RaidBossFastMeleeEnemy4`, `RaidBossMeleeEnemy1`, `RaidBossMeleeEnemy2`, `RaidBossMeleeEnemy3`, `RaidBossMeleeEnemy4`, `RaidBossRangedEnemy1`
`RaidBossRangedEnemy2`, `RaidBossRangedEnemy3`, `RaidBossRangedEnemy4`, `RaidBoss_TownCrush`, `RandomLootBox`, `RangedBot`, `Redirecter`, `RedirecterCocoon`
`RedirecterSnakePet`, `Reviver`, `RoboWarsBase`, `RoboWarsBox`, `RoboWarsRobo`, `Rock`, `RocketGirl`, `RocketGirlBuddy`
`Roller`, `RopeDude`, `Rosa`, `Ruffs`, `RuffsCover`, `Safe`, `SafeDeepsea`, `SafeKatanaKingdom`
`SafeVoxel`, `Samurai`, `SamuraiBoss`, `SamuraiFastMeleeEnemy`, `SamuraiMeleeEnemy`, `SamuraiRangedEnemy`, `Sandstorm`, `ShadowSmashSpider`
`Shadowdemon`, `ShadowdemonEnemy`, `Shaman`, `ShamanBuddy`, `ShamanPet`, `ShieldTank`, `ShotgunGirl`, `ShotgunGirlBuddy`
`Shuriken`, `Silencer`, `Skater`, `SnakeOil`, `Sniper`, `SoulCollector`, `SoulCollectorBuddy`, `SpawnerDude`
`SpawnerDudeTurret`, `SpawnerDudeTurret002`, `SpawnerDudeTurret003`, `SpawnerPet`, `SpawnerPet002`, `SpawnerPet003`, `SpawnerPetGadget`, `SpeedBooster`
`Speeder`, `Speedy`, `SpeedyBuddy`, `Splitter`, `SplitterLegs`, `Stacker`, `StackerMoth`, `StackerPet`
`Stalker`, `Starfish`, `StickyBomb`, `StuDrums`, `SubwayGuard`, `SuperNovaBeeSniper`, `SuperNovaCactus`, `SuperNovaCactusCover`
`SuperNovaFireDude`, `SuperNovaMagicalGirl`, `SuperNovaVoodoo`, `SuperNovaVoodooPet`, `SwarmHunterEnemy`, `SwarmSamuraiFastMeleeEnemy`, `SwarmSamuraiMeleeEnemy`, `SwarmSamuraiMeleeMiniBossEnemy`
`SwarmSamuraiRangedEnemy`, `TankArchetypeCover`, `TntDude`, `TntPet`, `Train0`, `Train1`, `Train2`, `Train3`
`TrainingDummyBig`, `TrainingDummyMedium`, `TrainingDummyShooting`, `TrainingDummySmall`, `TrickshotDude`, `TrickshotDudeBuddy`, `TrickshotDudeGadgetSkillContainer`, `TrickshotDudeGadgetSkillContainerBuddy`
`TrophyCritter`, `TutorialDummy`, `TutorialDummy2`, `TutorialDummy3`, `TutorialExplodingBarrel`, `Twins`, `TwinsPet`, `TwinsPetHyper`
`UNOCard`, `Undertaker`, `UndertakerBuddy`, `VolleyBall`, `VolleyBallZombie`, `Voodoo`, `VoodooPet`, `Wally`
`WeaponThrower`, `Whirlwind`

## 3. Тайлы / стены (`lookup(27, ...)`) — все 75

`ArenaConnector`, `Barrel`, `Base`, `Bouncer`, `Crate`, `Damage`
`Damageable1`, `Damageable2`, `Damageable3`, `Damageable4`, `DecoDestructible`, `Empty`
`ExtraBush`, `ExtraBushTemp`, `Fast`, `Fence`, `Forest`, `Fragile`
`GladiatorWallAstronaut`, `GladiatorWallDefault`, `GravityPull`, `GravityPush`, `Healing`, `Ice`
`Indestructible`, `IndestructibleDeco1`, `IndestructibleDeco2`, `IndestructibleDeco3`, `IndestructibleDeco4`, `IndestructibleFence`
`IntervalDamage`, `InvisibleIndestructible`, `InvisibleWater`, `MeepleWallDefault`, `MeepleWallDefault2`, `MeepleWallDefault3`
`Open`, `OutOfLineWall`, `OutOfLineWall_lvl3`, `PayloadTrack`, `PowerupCrate`, `ReSpawnPoint1`
`ReSpawnPoint2`, `RespawningForest`, `RopeFence`, `SiegeBolt`, `Slow`, `Snow`
`SpawnPoint1`, `SpawnPoint2`, `SpringBoard`, `Teleport1`, `Teleport2`, `Teleport3`
`Teleport4`, `Themed`, `Wall1`, `Wall2`, `WallyBathFillerWall`, `WallyBathWall`
`WallyDeepseaFillerWall`, `WallyDeepseaWall`, `WallyFillerWall`, `WallyMoonFillerWall`, `WallyMoonWall`, `WallyPrinceGreenFillerWall`
`WallyPrinceGreenWall`, `WallyPrinceRedFillerWall`, `WallyPrinceRedWall`, `WallyWall`, `WallyWeirdFillerWall`, `WallyWeirdWall`
`WallyWindstockFillerWall`, `WallyWindstockWall`, `Water`

## 4. Трейты (`lookup(108, ...)`)
Трейт добавляется через `char.traits:add(lookup(108, "Имя"))`. Обычно имя трейта = `<ИмяБойца><номер>` (например `Shelly1`, `Meg2_Transform`). Всего 1276 имён.

`8bit1`, `8bit2`, `8bit3`, `ASh3`, `ActorPlaceholderTrait`, `Amber1`, `Amber2`, `Amber3`, `Angelo1`, `Angelo2`
`Angels1_1`, `Angels1_2`, `Angels2_1`, `Angels2_2`, `Angels3_1`, `Angels4_1`, `Angels4_2`, `Angels5_1`, `Angels5_2`, `Angels6_1`
`Angels7_1`, `Angels8_1`, `Angels8_2`, `ArcadeGadget1HealPet`, `ArcadeGadget1HealSelf`, `ArcadeStarpower1PetComponent`, `ArcadeStarpower2ForTeammates`, `Ash1`, `Ash2`, `AssaultShotgunBuddySp1`
`AssaultShotgunBuddySp2`, `AssaultShotgunSp1_Salvo`, `AssaultShotgunSp1_Spread`, `AttractorOrbitSpeedStarPower`, `AttractorProjectileMagnet_OverrideTravelType`, `AttractorProjectileMagnet_SteerHomeDistance`, `AttractorProjectileMagnet_SteerIgnoreTicks`, `AttractorProjectileMagnet_SteerStrength`, `Barley1`, `BaseballSP2ExtraUltiDuration`
`Bea1`, `Belle1`, `Belle2`, `Belle3`, `Belle4`, `Berry1`, `Bo1`, `Bo2`, `Bonnie1`, `Bonnie2`
`Bonnie3`, `BowDudeSPHiddenDuringAttackInForest`, `BowDudeSPMineShotSpeed`, `Brock1`, `Brock2`, `Bull1`, `BullDudeBuddyTakedownShield`, `BullDude_Gadget_1`, `BullDude_Gadget_2`, `Buzz1`
`Buzz2`, `Buzz3`, `Byron1`, `Byron2`, `Carl1`, `Carl2`, `Charlie1`, `Colette1`, `Colette2`, `ColetteLifestealBuddyOverheal`
`Colt1`, `Colt2`, `ColtBuddySp1`, `ColtBuddySp2`, `ColtOverchargedProjectileBuff`, `ColtOverchargedProjectileBuff2`, `ColtSpeedSp`, `ConductorChargeSpeedBuddy`, `ConductorPoleFireBuddy`, `ConductorSlowSp`
`ConductorSp2ChargeAmmoSteal`, `ConductorStartWithFullUlti`, `Crow1`, `Crow2`, `CrowBuddySp1`, `CrowBuddySp2`, `CrowGadgetDaggerSlow`, `DeadMariachiProjectileHealPassive`, `DemogorgonLifeSteal`, `Demons1_1`
`Demons1_2`, `Demons1_3`, `Demons2_1`, `Demons2_2`, `Demons3_1`, `Demons3_2`, `Demons4_1`, `Demons5_1`, `Demons6_1`, `Demons6_2`
`Demons7_1`, `Demons8_1`, `Demons8_2`, `DisableVisionInBush`, `Draco1`, `DuplicatorPet1`, `Edgar1`, `Edgar2`, `Emz1`, `EmzBuddySp1`
`EmzBuddySp2`, `EnragerBuddySp1`, `EnragerBuddySp2`, `Eve1`, `Fang1`, `Fang2`, `Fang3`, `Finx1`, `FireDudeLongerFireBuddy`, `FireDudeSpBuddyPetrolStatus`
`FireDudeSpPetrolStatusEnemy`, `Frank1`, `Frank2`, `Frank3`, `FrankBuddySp1`, `FutureGirlSP1TurretAreaEffectEnemySlowdown`, `FutureGirlShieldDamageEnemy`, `FutureGirlTraitShieldOnMoving`, `FutureGirlTraitShieldOnSpawn`, `Gale1`
`Gene1`, `Gene2`, `Gene3`, `Gene4`, `Gene5`, `Gene6`, `GhostDeadCenterBoost`, `GhostDeadCenterBoostOvercharged`, `GhostDeadCenterGadgetCooldownBuddy`, `GhostLongerIncorporealBuddy`
`GladiatorOverrideChargeUpMax`, `GladiatorOverrideChargeUpType`, `Gladiator_SpawnFireAreaExplosionOnExpire`, `Gladiator_SpawnFireAreaOnExpire`, `Gray1`, `Gray2`, `Griff1`, `Griff2`, `Grom1`, `Grom2`
`Gus1`, `Gus2`, `Gus3`, `Hank1`, `HunterSurvivor_Damage`, `HunterSurvivor_HP`, `HunterSurvivor_Revive`, `HunterSurvivor_Scale`, `HunterSurvivor_Show`, `HunterSurvivor_Show_Survivor`
`HunterSurvivor_Speed`, `IgnoreStatusEffects`, `Jae1`, `Jae2`, `Janet1`, `Janet2`, `Jessie1`, `Jessie2`, `Jessie3`, `Juju1`
`Juju2`, `KatanaKidUltiAreaSizeBoost`, `Kenji1`, `Leon1`, `Leon2`, `Leon3`, `Leon4`, `Leon5`, `Lily1`, `Lily2`
`Lily3`, `Lily4`, `Lola1`, `Lola2`, `Lola3`, `Lola4`, `LuchadorThrowLandDamageEffect`, `MB_CCImmunity`, `MB_Colette_ProjectilSize`, `MB_Crow_FireBallAround`
`MB_Crow_ProjectileSpeed`, `MB_DragonCrowL1_ProjectilSize`, `MB_DragonCrowL2_ProjectilSize`, `MB_DragonCrowL3_ProjectilSize`, `MB_Duo_AreaEffectSize_20P`, `MB_Duo_AreaEffectSize_5P`, `MB_Duo_ProjectilSize_20P`, `MB_Duo_ProjectilSize_5P`, `MB_Duo_Shield`, `MB_FinxL1_ProjectilSize`
`MB_FinxL2_AreaSize`, `MB_FinxL2_ProjectilSize`, `MB_FinxTowerAreaEffect`, `MB_FinxTowerAreaSize`, `MB_FinxTowerUntargetable`, `MB_Griff_ProjectilSize`, `MB_Grom_AreaEffectSize`, `MB_Grom_BulletSize`, `MB_Grom_EffectSize`, `MB_KatanaKidFishSpawnerAreaSize`
`MB_KatanaKidFishSpawnerUntargetable`, `MB_Nita_ProjectilSize`, `MB_Rico_BulletExplode_1`, `MB_Rico_BulletExplode_2`, `MB_Rico_BulletExplode_3`, `MB_Shade_PassWall`, `MB_StickyBomb_Slow`, `Maisie1`, `Maisie2`, `Maisie3`
`Maisie4`, `Maisie5`, `Maisie6`, `Maisie7`, `Mandy1`, `Mandy2`, `Max1`, `MechaDudeSpSpeedWithShield`, `Meeple1`, `Meeple2`
`Meeple3`, `Meeple4`, `Meeple5`, `Meeple6`, `Meeple7`, `Meg1`, `Meg1_Transform`, `Meg2_Transform`, `Melodie1`, `Melodie2`
`Mod_speedup`, `Moe1`, `Moe1_Transform`, `Moe2`, `Mortis1`, `MortisBuddySp1`, `MortisBuddySp2`, `MrP1`, `Nano_8Bit_AreaSize`, `Nano_8Bit_MoveSpeed`
`Nano_8Bit_ProjectileSpeed`, `Nano_Alli_Damage`, `Nano_Alli_Reload`, `Nano_Alli_Water`, `Nano_Amber_Range`, `Nano_Amber_Reload`, `Nano_Amber_Super_1`, `Nano_Amber_Super_2`, `Nano_Angelo_HoldTime`, `Nano_Angelo_Super_Area`
`Nano_Angelo_Super_Damage`, `Nano_Angelo_Swap`, `Nano_Ash_Homein_1`, `Nano_Ash_Homein_2`, `Nano_Ash_Homein_3`, `Nano_Ash_Homein_4`, `Nano_Ash_PetNumber_1`, `Nano_Ash_PetNumber_2`, `Nano_Ash_Rage`, `Nano_Barley_Attack_Size_1`
`Nano_Barley_Attack_Size_2`, `Nano_Barley_Poison`, `Nano_Barley_Super_Time_1`, `Nano_Barley_Super_Time_2`, `Nano_Bea_Attack_1`, `Nano_Bea_Attack_2`, `Nano_Bea_Attack_3`, `Nano_Bea_Attack_4`, `Nano_Bea_Chain_Slow`, `Nano_Bea_Shield`
`Nano_Bea_Super_Charge`, `Nano_Bea_Super_Damage`, `Nano_Belle_Chain_1`, `Nano_Belle_Chain_2`, `Nano_Belle_Gadget`, `Nano_Belle_Super`, `Nano_Berry_Attack_Size_1`, `Nano_Berry_Attack_Size_2`, `Nano_Berry_Heal_Self`, `Nano_Berry_Heal_Team`
`Nano_Berry_Super_Effect`, `Nano_Berry_Super_Range`, `Nano_Berry_Super_Shield`, `Nano_Bibi_Range_1`, `Nano_Bibi_Range_2`, `Nano_Bibi_Shield_1`, `Nano_Bibi_Shield_2`, `Nano_Bibi_Super_1`, `Nano_Bibi_Super_2`, `Nano_Bibi_Super_3`
`Nano_Bo_Charge`, `Nano_Bo_Damage`, `Nano_Bo_InfinateMine`, `Nano_Bo_Mine_1`, `Nano_Bo_Mine_2`, `Nano_Bo_Range`, `Nano_Bolt_Attack`, `Nano_Bolt_Speedup`, `Nano_Bolt_Super_Area`, `Nano_Bolt_Super_Effect_Speed`
`Nano_Bolt_Super_Last`, `Nano_Bonnie_Attack`, `Nano_Bonnie_Charge_1`, `Nano_Bonnie_Charge_2`, `Nano_Bonnie_Speed`, `Nano_Brock_Area_1`, `Nano_Brock_Area_2`, `Nano_Brock_Gadget`, `Nano_Brock_Super`, `Nano_Bull_Attack_Pattern`
`Nano_Bull_Attack_Spread`, `Nano_Bull_ChargeSpeed`, `Nano_Bull_Execute`, `Nano_Buster_ActiveTime`, `Nano_Buster_Bullet`, `Nano_Buster_ReflectDamage`, `Nano_Buster_Spread`, `Nano_Buzz_Attack_Range`, `Nano_Buzz_Attack_Size`, `Nano_Buzz_HC_Rate`
`Nano_Buzz_HC_Time`, `Nano_Buzz_Super_Projectile`, `Nano_Buzz_Super_Range`, `Nano_Buzz_Super_Speed`, `Nano_Byron_HealCharge`, `Nano_Byron_HomeIn_1`, `Nano_Byron_HomeIn_2`, `Nano_Byron_HomeIn_3`, `Nano_Byron_HomeIn_4`, `Nano_Byron_Super_Projectile`
`Nano_Byron_Super_Push`, `Nano_Byron_Super_Size`, `Nano_Carl_Attack_Size`, `Nano_Carl_Fire`, `Nano_Carl_Super_Area_1`, `Nano_Carl_Super_Area_2`, `Nano_Carl_Super_Speed`, `Nano_Charlie_Cocoon_HP`, `Nano_Charlie_Cocoon_HealthBack`, `Nano_Charlie_Cocoon_Size`
`Nano_Charlie_Projectile_Size`, `Nano_Charlie_Projectile_Speed`, `Nano_Charlie_Spider`, `Nano_Chester_Attack`, `Nano_Chester_Charge_1`, `Nano_Chester_Charge_2`, `Nano_Chester_HC`, `Nano_Chuck_Attack_Size`, `Nano_Chuck_Charge`, `Nano_Chuck_Pole`
`Nano_Chuck_Super_Damage`, `Nano_Chuck_Super_Effect`, `Nano_Chuck_Super_Speed`, `Nano_Clancy_Level`, `Nano_Clancy_Range`, `Nano_Clancy_Super_1`, `Nano_Clancy_Super_2`, `Nano_Clancy_Super_3`, `Nano_Colette_Damage`, `Nano_Colette_Size`
`Nano_Colette_Super_Area`, `Nano_Colette_Super_Damage`, `Nano_Colt_Bounce_1`, `Nano_Colt_Bounce_2`, `Nano_Colt_Bounce_3`, `Nano_Colt_MoveSpeed`, `Nano_Colt_Pierce`, `Nano_Colt_Super_Size`, `Nano_Cordelius_Attack`, `Nano_Cordelius_Charge`
`Nano_Cordelius_Home_1`, `Nano_Cordelius_Home_2`, `Nano_Cordelius_Home_3`, `Nano_Cordelius_Home_4`, `Nano_Cordelius_Mushroom`, `Nano_Crow_Attack_Bullet`, `Nano_Crow_Attack_Spread`, `Nano_Crow_StatusEffect`, `Nano_Crow_Super`, `Nano_Damian_FirePunch`
`Nano_Damian_Range`, `Nano_Damian_Size`, `Nano_Damian_Super`, `Nano_Darryl_Attack_Swap`, `Nano_Darryl_Cons_Shield`, `Nano_Darryl_Super_Damage`, `Nano_Darryl_Super_Time`, `Nano_Doug_Attack`, `Nano_Doug_Item`, `Nano_Doug_Super`
`Nano_Draco_Fire`, `Nano_Draco_Range`, `Nano_Draco_Time`, `Nano_Dynamike_Attack`, `Nano_Dynamike_Delay`, `Nano_Dynamike_SuperSize_1`, `Nano_Dynamike_SuperSize_2`, `Nano_Edgar_Effect`, `Nano_Edgar_Gadget`, `Nano_Edgar_Range`
`Nano_Edgar_Size`, `Nano_Edgar_Super_Charge`, `Nano_Edgar_Super_HC`, `Nano_Emz_Attack`, `Nano_Emz_Attack_Effect`, `Nano_Emz_Special`, `Nano_Emz_Super`, `Nano_Eve_Attack_ActiveTime`, `Nano_Eve_Attack_Bullet`, `Nano_Eve_Attack_Damage`
`Nano_Eve_Passive`, `Nano_Eve_Super_1`, `Nano_Eve_Super_2`, `Nano_Fang_Attack_Area`, `Nano_Fang_Attack_Chain_1`, `Nano_Fang_Attack_Chain_2`, `Nano_Fang_Attack_Chain_3`, `Nano_Fang_Heal_OnKill`, `Nano_Fang_Super_Effect`, `Nano_Fang_Super_Shield`
`Nano_Finx_Area`, `Nano_Finx_Attack`, `Nano_Finx_Duration`, `Nano_Finx_FollowArea`, `Nano_Frank_Attack`, `Nano_Frank_HP`, `Nano_Frank_Scale`, `Nano_Frank_Speed`, `Nano_Frank_Spread`, `Nano_Frank_Super_Range`
`Nano_Gale_Attck_MoreBullet`, `Nano_Gale_Freeze_Attack`, `Nano_Gale_Freeze_Super`, `Nano_Gale_Super_MoreBullet`, `Nano_Gene_Chain_Number`, `Nano_Gene_Chain_Spread`, `Nano_Gene_Super_Damage`, `Nano_Gene_Super_Range`, `Nano_Gene_Trigger`, `Nano_Gigi_Charge_Area_1`
`Nano_Gigi_Charge_Area_2`, `Nano_Gigi_MaxAmmo`, `Nano_Gigi_Super_1`, `Nano_Gigi_Super_2`, `Nano_Gigi_Super_3`, `Nano_Glowy_LOS`, `Nano_Glowy_Super_Status`, `Nano_Glowy_Tether_Double`, `Nano_Gray_Attack`, `Nano_Gray_Charge`
`Nano_Gray_Portal`, `Nano_Gray_Trigger`, `Nano_Griff_Range`, `Nano_Griff_Special`, `Nano_Griff_Super`, `Nano_Grom_Attack_Number`, `Nano_Grom_Chain_Distance`, `Nano_Grom_Chain_Effect`, `Nano_Grom_Size`, `Nano_Grom_Speed`
`Nano_Grom_Super_MS`, `Nano_Grom_Super_Time`, `Nano_Gus_Balloon_1`, `Nano_Gus_Balloon_2`, `Nano_Gus_Balloon_3`, `Nano_Gus_Size`, `Nano_Gus_Size_Item`, `Nano_Gus_Super_Shield_Amount`, `Nano_Gus_Super_Shield_Decay`, `Nano_Gus_Super_Shield_Size`
`Nano_Hank_Range_1`, `Nano_Hank_Range_2`, `Nano_Hank_Range_3`, `Nano_Hank_Super_BulletNumber`, `Nano_Hank_Super_Heal`, `Nano_Hank_Trigger`, `Nano_Jacky_Attack_Range`, `Nano_Jacky_Charge`, `Nano_Jacky_Super_Shield`, `Nano_Jae_Area`
`Nano_Jae_Attack`, `Nano_Jae_Charge`, `Nano_Janet_Jetpack`, `Nano_Janet_Range`, `Nano_Janet_Super_Attack`, `Nano_Jessie_Chain_1`, `Nano_Jessie_Chain_2`, `Nano_Jessie_ShootTwice_1`, `Nano_Jessie_ShootTwice_2`, `Nano_Jessie_SuperUse`
`Nano_Jessie_Super_MaxSpawn`, `Nano_Juju_Area`, `Nano_Juju_AutoCharge`, `Nano_Juju_Damage`, `Nano_Juju_Grigri_Attack`, `Nano_Juju_Grigri_Size`, `Nano_Juju_Grigri_Speed`, `Nano_Juju_Range`, `Nano_Kaze_Attack_1`, `Nano_Kaze_Attack_2`
`Nano_Kaze_Attack_3`, `Nano_Kaze_Range_1`, `Nano_Kaze_Range_2`, `Nano_Kaze_Shield`, `Nano_Kaze_Super`, `Nano_Kenji_Heal`, `Nano_Kenji_Range_Effect`, `Nano_Kenji_Range_Slash`, `Nano_Kenji_Super_Rate`, `Nano_Kenji_Super_Size`
`Nano_Kenji_Super_Teleport`, `Nano_Kit_Attach`, `Nano_Kit_PowerCubeOnKill`, `Nano_Kit_Range_1`, `Nano_Kit_Range_2`, `Nano_Larry_Pet_1`, `Nano_Larry_Pet_2`, `Nano_Larry_Pet_3`, `Nano_Larry_Reborn`, `Nano_Larry_Size_1`
`Nano_Larry_Size_2`, `Nano_Leon_Attack`, `Nano_Leon_Kill`, `Nano_Leon_Super_1`, `Nano_Leon_Super_2`, `Nano_Leon_Super_3`, `Nano_Lily_Attack_Ammo`, `Nano_Lily_Gadget`, `Nano_Lily_Super_Damage`, `Nano_Lily_Super_Home_1`
`Nano_Lily_Super_Home_2`, `Nano_Lily_Super_Home_3`, `Nano_Lily_Super_Home_4`, `Nano_Lola_Attack`, `Nano_Lola_Pet_1`, `Nano_Lola_Pet_2`, `Nano_Lola_Special`, `Nano_Lou_Attack_Size`, `Nano_Lou_Freeze_Super`, `Nano_Lou_Super_Size`
`Nano_Lumi_Attack_Size`, `Nano_Lumi_Item_Size`, `Nano_Lumi_Projectile_Speed`, `Nano_Lumi_Super_Size`, `Nano_Maisie_Dash`, `Nano_Maisie_Super`, `Nano_Maisie_Super_Charge`, `Nano_Maisie_Swap`, `Nano_Mandy_Attack_Range`, `Nano_Mandy_Camera_Distance`
`Nano_Mandy_Camera_Vision`, `Nano_Mandy_Super_Rate`, `Nano_Mandy_Super_Size`, `Nano_Max_Projectile_Speed`, `Nano_Max_Reload`, `Nano_Max_Super_Speedup`, `Nano_Meeple_Area_1`, `Nano_Meeple_Area_2`, `Nano_Meeple_Duration`, `Nano_Meeple_HomeInMore`
`Nano_Meg_Attack`, `Nano_Meg_HP`, `Nano_Meg_Scale`, `Nano_Meg_Spread`, `Nano_Meg_Super_1`, `Nano_Meg_Super_2`, `Nano_Meg_Super_3`, `Nano_Melodie_Attack_Chain`, `Nano_Melodie_Notes`, `Nano_Melodie_Orbit_Faster`
`Nano_Melodie_Orbit_Larger`, `Nano_Melodie_SuperUse`, `Nano_Melodie_Super_ChargeSpeed`, `Nano_Merge_General`, `Nano_Merge_General_Meg`, `Nano_Mico_Range`, `Nano_Mico_Reload`, `Nano_Mico_Super_Damage`, `Nano_Mico_Super_Size`, `Nano_Mina_Heal`
`Nano_Mina_Reload`, `Nano_Mina_Shield`, `Nano_Moe_Attack_Damage`, `Nano_Moe_Attack_Range`, `Nano_Moe_Drill`, `Nano_Moe_Drill_Range`, `Nano_Moe_Super_Charge`, `Nano_Mortis_DashSpeed`, `Nano_Mortis_Heal`, `Nano_Mortis_Range`
`Nano_Mortis_Super_Rate`, `Nano_Mrp_Attack_Area`, `Nano_Mrp_Attack_Size`, `Nano_Mrp_Spawn`, `Nano_Mrp_Super_Passive`, `Nano_Najia_HP`, `Nano_Najia_HealthBack`, `Nano_Najia_Pierce`, `Nano_Najia_Range`, `Nano_Najia_Trigger`
`Nano_Nani_Attack_Bullet`, `Nano_Nani_Attack_Damage`, `Nano_Nani_Attack_Spread`, `Nano_Nani_Reflect`, `Nano_Nani_Super_Damage`, `Nano_Nani_Super_Time`, `Nano_Nita_Attack`, `Nano_Nita_Bear_HP`, `Nano_Nita_Bear_Size`, `Nano_Nita_Super_Auto`
`Nano_Nori_Attack`, `Nano_Nori_Fish`, `Nano_Nori_Super`, `Nano_Olli_Bullet`, `Nano_Olli_Damage`, `Nano_Olli_Gadget`, `Nano_Olli_Spread`, `Nano_Olli_Taunt`, `Nano_Otis_ActiveTime`, `Nano_Otis_Duration`
`Nano_Otis_Super_Pierce_1`, `Nano_Otis_Super_Pierce_2`, `Nano_Pam_AreaSize`, `Nano_Pam_Health`, `Nano_Pam_HomeIn`, `Nano_Pam_Size`, `Nano_Pearl_Attack`, `Nano_Pearl_Heat`, `Nano_Pearl_Projectile`, `Nano_Pearl_Spread`
`Nano_Pearl_Super_Area`, `Nano_Pearl_Swap`, `Nano_Penny_AttackSpeed`, `Nano_Penny_Chain_1`, `Nano_Penny_Chain_2`, `Nano_Penny_Super_1`, `Nano_Penny_Super_2`, `Nano_Pierce_ChargeShoot_Pierce`, `Nano_Pierce_ChargeShoot_Size`, `Nano_Pierce_DropShell`
`Nano_Pierce_Super_Size`, `Nano_Piper_Attack_FarDamage`, `Nano_Piper_SuperRate`, `Nano_Piper_SuperSpeed`, `Nano_Piper_Swap`, `Nano_Poco_Bullet`, `Nano_Poco_Damage`, `Nano_Poco_Pattern`, `Nano_Poco_Spread`, `Nano_Poco_Super_Heal`
`Nano_Poco_Super_Heal_Self`, `Nano_Poco_Super_Range`, `Nano_Primo_Attack_Speed`, `Nano_Primo_Charge_HC`, `Nano_Primo_Charge_Ulti`, `Nano_Primo_Range`, `Nano_Primo_Super_Effect`, `Nano_Primo_Super_Size`, `Nano_RT_Bullet_Area`, `Nano_RT_Mark_Damage`
`Nano_RT_Swap`, `Nano_Rico_BulletSize`, `Nano_Rico_Super_Bounce_1`, `Nano_Rico_Super_Bounce_2`, `Nano_Rico_Super_Bounce_3`, `Nano_Rico_Trigger`, `Nano_Rosa_Bush_Damage`, `Nano_Rosa_Bush_Speed`, `Nano_Rosa_Effect`, `Nano_Rosa_Shield`
`Nano_Rosa_SpawnBushOnAttack`, `Nano_Ruff_Bullet`, `Nano_Ruff_HC`, `Nano_Ruff_Super_Damage`, `Nano_Ruff_Super_Size`, `Nano_Sam_Attack`, `Nano_Sam_Charge`, `Nano_Sam_Slow`, `Nano_Sandy_Range`, `Nano_Sandy_Super`
`Nano_Sandy_Trigger`, `Nano_Sandy_Trigger_Effect`, `Nano_Shade_AttackRange_1`, `Nano_Shade_AttackRange_2`, `Nano_Shade_Charge`, `Nano_Shade_SuperLastTime`, `Nano_Shelly_Attack_Range`, `Nano_Shelly_Attack_Spread`, `Nano_Shelly_Heal`, `Nano_Shelly_Super_Double_1`
`Nano_Shelly_Super_Double_2`, `Nano_Shelly_Super_Double_3`, `Nano_Shelly_Super_Double_4`, `Nano_Sirius_Area_1`, `Nano_Sirius_Area_2`, `Nano_Sirius_Clone_HP`, `Nano_Sirius_Clone_Size`, `Nano_Sirius_Spawn_Teammate`, `Nano_Sirius_Super_Max_Clone`, `Nano_Sirius_Super_Max_Hord`
`Nano_Spike_BulletMore`, `Nano_Spike_Revive`, `Nano_Spike_Super_1`, `Nano_Spike_Super_2`, `Nano_Sprout_Attack_Area`, `Nano_Sprout_Attack_Size`, `Nano_Sprout_Super_Damage`, `Nano_Sprunt_Passive`, `Nano_Squeak_Attack`, `Nano_Squeak_Size_1`
`Nano_Squeak_Size_2`, `Nano_Squeak_SpawnArea`, `Nano_Starrnova_Attack_Range_1`, `Nano_Starrnova_Attack_Range_2`, `Nano_Starrnova_Duration`, `Nano_Starrnova_Super_Effect`, `Nano_Starrnova_Super_Range`, `Nano_Stu_Attack_Reload`, `Nano_Stu_HC`, `Nano_Stu_Super`
`Nano_Surge_Attack`, `Nano_Surge_Super_Area_1`, `Nano_Surge_Super_Area_2`, `Nano_Surge_Super_Range`, `Nano_Surge_Super_Slow`, `Nano_Surge_Trait`, `Nano_Tara_Attack_Bullet`, `Nano_Tara_Attack_Spread`, `Nano_Tara_Spawn`, `Nano_Tara_Super_1`
`Nano_Tara_Super_2`, `Nano_Tick_BulleNumber`, `Nano_Tick_Head_1`, `Nano_Tick_Head_2`, `Nano_Tick_PetMax_BigHead`, `Nano_Tick_PetMax_Damage`, `Nano_Tick_PetMax_HP`, `Nano_Tick_PetMax_ProjectileSize`, `Nano_Tick_PetMax_Scale`, `Nano_Trunk_Attack_Area`
`Nano_Trunk_Super_Range`, `Nano_Trunk_Trigger`, `Nano_Wendy_Pet_HP`, `Nano_Wendy_Pet_Size`, `Nano_Wendy_Pierce`, `Nano_Wendy_Shield_Reload`, `Nano_Willow_Damage`, `Nano_Willow_Size_1`, `Nano_Willow_Size_2`, `Nano_Willow_Super_Pierce`
`Nano_Willow_Super_Range`, `Nano_Ziggy_Attack`, `Nano_Ziggy_Slow`, `Nano_Ziggy_Super`, `NinjaBuddySp1`, `NinjaBuddySp2`, `Nita1`, `Nita2`, `Nita3`, `Olli1`
`Olli2`, `Pearl1`, `Pearl2`, `Pearl3`, `Penny1`, `Penny2`, `Penny4`, `PercenterBuddySp1`, `PercenterBuddySp2`, `PercenterOverchargeFollowupProjectile`
`PercenterSp2ChargeDamageReduction`, `Piper1`, `Piper2`, `Poco1`, `PocoBuddySp1`, `PocoBuddySp2`, `PowerLevelerBouncyProjectilesSp`, `PowerLevelerBouncyProjectilesSpBuddy`, `PowerLevelerSpeedBurstOnUltiAt2`, `PowerLevelerStartWithUltiInitial`
`PowerLevelerStartWithUltiRespawn`, `R_8Bit_Speed_L`, `R_Add_Bullets_BasicAttack_L_1`, `R_Add_Bullets_BasicAttack_L_2`, `R_Add_Bullets_BasicAttack_ULTRA_1`, `R_Add_Bullets_BasicAttack_ULTRA_2`, `R_Angelo_Area_L`, `R_Angelo_HoldTime_L`, `R_AreaEffectSizeThrower_E`, `R_AreaEffectSizeThrower_L`
`R_AreaEffectSizeThrower_Mini_E`, `R_AreaEffectSizeThrower_Mini_L`, `R_AreaEffectSizeThrower_Mini_S`, `R_AreaEffectSizeThrower_S`, `R_AreaEffectSize_E`, `R_AreaEffectSize_L`, `R_AreaEffectSize_Melee_E`, `R_AreaEffectSize_Melee_L`, `R_AreaEffectSize_Melee_S`, `R_AreaEffectSize_Mini_E`
`R_AreaEffectSize_Mini_L`, `R_AreaEffectSize_Mini_S`, `R_AreaEffectSize_S`, `R_AreaEffectSize_ULTRA`, `R_AreaEffect_BulletSize_E_1`, `R_AreaEffect_BulletSize_E_2`, `R_AreaEffect_BulletSize_L_1`, `R_AreaEffect_BulletSize_L_2`, `R_AreaEffect_BulletSize_S_1`, `R_AreaEffect_BulletSize_S_2`
`R_Ash_PetNumber_L_1`, `R_Ash_PetNumber_L_2`, `R_AttackRange_Cone_E_1`, `R_AttackRange_Cone_E_2`, `R_AttackRange_Cone_E_3`, `R_AttackRange_Cone_L_1`, `R_AttackRange_Cone_L_2`, `R_AttackRange_Cone_L_3`, `R_AttackRange_Cone_Mini_L_1`, `R_AttackRange_Cone_Mini_L_2`
`R_AttackRange_Cone_Mini_L_3`, `R_AttackRange_E`, `R_AttackRange_L`, `R_AttackRange_Max_L`, `R_AttackRange_Mini_L`, `R_AttackRange_ULTRA`, `R_AutoChargeUlti_E`, `R_AutoChargeUlti_L`, `R_AutoChargeUlti_Max_E`, `R_AutoChargeUlti_Max_L`
`R_AutoChargeUlti_Sam_E`, `R_Barley_Slow_L`, `R_Bea_Shield_L`, `R_Berry_L`, `R_Bibi_Range_L_1`, `R_Bibi_Range_L_2`, `R_Bo_InfinateMine_L`, `R_Bo_MainAtkMore_L`, `R_Boomerang_L`, `R_Brock_L`
`R_Bull_L`, `R_BulletSizeArea_Mini_WithItem_E`, `R_BulletSizeArea_Mini_WithItem_L`, `R_BulletSizeArea_Mini_WithItem_S`, `R_BulletSizeThrower_E`, `R_BulletSizeThrower_L`, `R_BulletSizeThrower_Mini_E`, `R_BulletSizeThrower_Mini_L`, `R_BulletSizeThrower_Mini_S`, `R_BulletSizeThrower_S`
`R_BulletSize_E`, `R_BulletSize_L`, `R_BulletSize_Max_E`, `R_BulletSize_Max_L`, `R_BulletSize_Max_S`, `R_BulletSize_Mini_E`, `R_BulletSize_Mini_L`, `R_BulletSize_Mini_S`, `R_BulletSize_S`, `R_BulletSize_ULTRA`
`R_BurnOnHit_E`, `R_BurnOnHit_Hold_E`, `R_BurnOnHit_Hold_L`, `R_BurnOnHit_Hold_S`, `R_BurnOnHit_L`, `R_BurnOnHit_S`, `R_Buster_ActiveTime_L`, `R_Buzz_SuperRange_L_1`, `R_Buzz_SuperRange_L_2`, `R_Byron_StatusEffect_L`
`R_Carl_Reload_L`, `R_ChargeHCOnStart_E`, `R_ChargeHCOnStart_L`, `R_ChargeHCOnStart_Mini_L`, `R_ChargeSuperOnStart_E`, `R_ChargeSuperOnStart_S`, `R_ChargeUpSpeed_L`, `R_Charlie_Spider_L`, `R_Chuck_Pole_E`, `R_Chuck_Pole_L`
`R_Chuck_Super_E`, `R_Clancy_Level_L`, `R_Codilus_MainAtk_L`, `R_Colt_MoreBullet_L`, `R_ConsShield`, `R_ConsShield_Mini`, `R_DOT_E`, `R_DOT_L`, `R_DamageReduction_E`, `R_DamageReduction_Effect_E`
`R_DamageReduction_Effect_L`, `R_DamageReduction_L`, `R_DamageReduction_Max_L`, `R_DamageReduction_Mini_E`, `R_DamageReduction_Mini_L`, `R_DamageReduction_Mini_S`, `R_DamageReduction_S`, `R_Damage_E`, `R_Damage_L`, `R_Damage_Mini_E`
`R_Damage_Mini_L`, `R_Damage_Mini_S`, `R_Damage_S`, `R_Damage_ULTRA`, `R_DashSpeed_E`, `R_DashSpeed_Mini_E`, `R_DashSpeed_Mini_L`, `R_DestroyEnvironment`, `R_Draco_Super_L`, `R_Dynamike_Delay_L`
`R_Emz_Area_L`, `R_Eve_PetNumber_L_1`, `R_Eve_PetNumber_L_2`, `R_Eve_TriggerSuper_MoreTimes_L_1`, `R_Eve_TriggerSuper_MoreTimes_L_2`, `R_FireBallAround_E`, `R_FireBallAround_L`, `R_Frank_HP_L`, `R_Frank_Scale_E`, `R_Frank_Scale_L`
`R_Frank_Scale_S`, `R_Frank_SpeedDown_E`, `R_Frank_SpeedDown_L`, `R_Frank_SpeedDown_S`, `R_GadgetCooldown_E`, `R_GadgetCooldown_L`, `R_GadgetCooldown_Mini_E`, `R_GadgetCooldown_Mini_L`, `R_GadgetCooldown_Mini_Min_E`, `R_GadgetCooldown_Mini_Min_L`
`R_GadgetCooldown_Mini_Min_S`, `R_GadgetCooldown_Mini_S`, `R_GadgetCooldown_S`, `R_Gale_MoreBullet_E_1`, `R_Gale_MoreBullet_E_2`, `R_Gale_MoreBullet_L_1`, `R_Gale_MoreBullet_L_2`, `R_Gale_MoreBullet_S`, `R_Gene_SuperRange_L`, `R_God_Max_ScaleUp`
`R_God_ScaleUp`, `R_Gus_L_1`, `R_Gus_L_2`, `R_Gus_L_3`, `R_HCRate_E`, `R_HCRate_L`, `R_HCRate_Mini_E`, `R_HCRate_Mini_L`, `R_HCRate_Mini_S`, `R_HCRate_S`
`R_HCTime_L`, `R_Hank_L`, `R_Hank_Range_E_1`, `R_Hank_Range_E_2`, `R_Hank_Range_E_3`, `R_Hank_Range_L_1`, `R_Hank_Range_L_2`, `R_Hank_Range_L_3`, `R_Hank_Range_S_1`, `R_Hank_Range_S_2`
`R_Hank_Range_S_3`, `R_HealBuff_E`, `R_HealBuff_L`, `R_HealBuff_Mini_E`, `R_HealBuff_Mini_L`, `R_HealBuff_Mini_S`, `R_HealBuff_S`, `R_HealOnKill`, `R_HealOnMove`, `R_HighHealthDamage_E`
`R_HighHealthDamage_L`, `R_HomeInOnAtk_1`, `R_HomeInOnAtk_2`, `R_HomeInOnAtk_3`, `R_HomeInOnAtk_4`, `R_HomeInOnAtk_Max_1`, `R_HomeInOnAtk_Melee_1`, `R_HomeInOnAtk_Melee_2`, `R_HomeInOnAtk_Melee_3`, `R_HomeInOnAtk_Melee_4`
`R_HomeInOnUlti_1`, `R_HomeInOnUlti_2`, `R_HomeInOnUlti_3`, `R_HomeInOnUlti_4`, `R_InvisibleOnKill`, `R_Janet_ActiveTime_E`, `R_Janet_ActiveTime_L`, `R_Kaze_EffectSize_E`, `R_Kaze_EffectSize_L`, `R_Kaze_EffectSize_S`
`R_Kit_AttackRange_L_1`, `R_Kit_AttackRange_L_2`, `R_Kit_AttackRange_L_3`, `R_Kit_PowerCube_E`, `R_KnockbackOnTakeDmg`, `R_Leon_Super_L`, `R_LifeSteal_E`, `R_LifeSteal_L`, `R_LifeSteal_Mini_E`, `R_LifeSteal_Mini_L`
`R_LifeSteal_Mini_S`, `R_LifeSteal_Pet_E`, `R_LifeSteal_Pet_L`, `R_LifeSteal_Pet_S`, `R_LifeSteal_S`, `R_LowHealthDamage_E`, `R_LowHealthDamage_L`, `R_LowHealthDamage_Mini_L`, `R_Lumi_L`, `R_MaxHp_Absolute_E`
`R_MaxHp_Absolute_L`, `R_MaxHp_Absolute_Meg_E`, `R_MaxHp_Absolute_Meg_L`, `R_MaxHp_Absolute_Meg_S`, `R_MaxHp_Absolute_Mini_E`, `R_MaxHp_Absolute_Mini_L`, `R_MaxHp_Absolute_Mini_Mini_E`, `R_MaxHp_Absolute_Mini_Mini_L`, `R_MaxHp_Absolute_Mini_Mini_S`, `R_MaxHp_Absolute_Mini_S`
`R_MaxHp_Absolute_S`, `R_MaxHp_Absolute_ULTRA`, `R_MaxHp_E`, `R_MaxHp_L`, `R_MaxHp_S`, `R_Meeple_HomeInMore_L`, `R_Melodie_Notes_E`, `R_Melodie_Notes_L`, `R_Mina_Shield_L`, `R_Mortis_Dash_E_1`
`R_Mortis_Dash_E_2`, `R_Mortis_Dash_L_1`, `R_Mortis_Dash_L_2`, `R_MoveSpeedInBush_E`, `R_MoveSpeedInBush_Mini_E`, `R_MoveSpeedInBush_Mini_S`, `R_MoveSpeedInBush_S`, `R_MoveSpeed_E`, `R_MoveSpeed_L`, `R_MoveSpeed_Max_L`
`R_MoveSpeed_Mini_E`, `R_MoveSpeed_Mini_L`, `R_MoveSpeed_Mini_Mini_E`, `R_MoveSpeed_Mini_Mini_L`, `R_MoveSpeed_Mini_Mini_S`, `R_MoveSpeed_Mini_S`, `R_MoveSpeed_S`, `R_MoveSpeed_ULTRA`, `R_MoveSpeed_WithPet_E`, `R_MoveSpeed_WithPet_L`
`R_MoveSpeed_WithPet_S`, `R_Nani_Bullets_L_1`, `R_Nani_Bullets_L_2`, `R_Nani_Super_E`, `R_Nani_Super_L`, `R_Nita_L`, `R_Olli_Bullet_L`, `R_Olli_Spread_L`, `R_Otis_ActiveTime_L`, `R_PassEnvironment`
`R_PetMaxHP_E_1`, `R_PetMaxHP_E_2`, `R_PetMaxHP_L_1`, `R_PetMaxHP_L_2`, `R_PetMaxHP_S_1`, `R_PetMaxHP_S_2`, `R_PetMoveSpeed_E`, `R_PetMoveSpeed_S`, `R_PetNumber_L_1`, `R_PetNumber_L_2`
`R_PierceCharacter`, `R_Poco_Heal_L`, `R_PoisonOnHit_E`, `R_PoisonOnHit_L`, `R_PoisonOnHit_S`, `R_PowerCubeDouble_L`, `R_PowerCubeEffective_E`, `R_PowerCubeEffective_L`, `R_PowerCubeOnKill`, `R_PowerCubeOnKillDouble_L`
`R_PowerCubeOnStart_E`, `R_PowerCubeOnStart_L`, `R_PowerCubeOnStart_S`, `R_PowerCubeOnStart_ULTRA`, `R_PowerCubeOnUlti`, `R_Primo_L`, `R_ProjectileSpeed_E`, `R_ProjectileSpeed_L`, `R_ProjectileSpeed_Max_E`, `R_ProjectileSpeed_Max_L`
`R_ProjectileSpeed_Max_S`, `R_ProjectileSpeed_S`, `R_RegenFaster`, `R_Reload_E`, `R_Reload_L`, `R_Reload_Mini_E`, `R_Reload_Mini_L`, `R_Reload_Mini_S`, `R_Reload_S`, `R_Rico_Bounce_E_1`
`R_Rico_Bounce_E_2`, `R_Rico_Bounce_E_3`, `R_Rico_Bounce_E_4`, `R_Rico_Bounce_L_1`, `R_Rico_Bounce_L_2`, `R_Rico_Bounce_L_3`, `R_Rico_Bounce_L_4`, `R_Rico_Bounce_S_1`, `R_Rico_Bounce_S_2`, `R_Rico_Bounce_S_3`
`R_Rico_Bounce_S_4`, `R_Ruff_Bounce_E_1`, `R_Ruff_Bounce_E_2`, `R_Ruff_Bounce_L_1`, `R_Ruff_Bounce_L_2`, `R_Ruff_Bounce_S_1`, `R_Ruff_Bounce_S_2`, `R_SeeThroghtBushOnSuper`, `R_Shade_AttackRange_L_1`, `R_Shade_AttackRange_L_2`
`R_Shade_SuperLastTime_L`, `R_Shelly_L_1`, `R_Shelly_L_2`, `R_ShootTwice_MainAtk_L_1`, `R_ShootTwice_MainAtk_L_2`, `R_ShootTwice_Throw_L`, `R_SlowDownOnHit`, `R_SpawnBushOnAttack_L`, `R_SpawnBushOnMove`, `R_SpeedUpOnAtk`
`R_SpeedUpOnGadget_S`, `R_SpeedUpOnSuper`, `R_Spike_BulletMore_E`, `R_Spike_BulletMore_L`, `R_Spread_L`, `R_Sprout_GadgetCooldown_L`, `R_Squeak_SpawnAreaE_L`, `R_SuperRate_E`, `R_SuperRate_L`, `R_SuperRate_Mini_E`
`R_SuperRate_Mini_L`, `R_SuperRate_Mini_S`, `R_SuperRate_S`, `R_Tick_BulleNumber_E`, `R_Tick_BulleNumber_L`, `R_TriggerSuper_MoreTimes_1_L`, `R_TriggerSuper_MoreTimes_Pet_L_1`, `R_TriggerSuper_MoreTimes_Pet_L_2`, `R_VisionInBush_E`, `R_VisionInBush_L`
`R_VisionInBush_S`, `RedirecterStarPowerCurrentHPPoisonTrait`, `RedirecterStarPowerSpawnPetOnTargetDeathTrait`, `Rico1`, `Rico2`, `RockChargeUltiOnMove`, `RocketGirlAddCastingRangeSP2`, `RocketGirlSP1SpeedBuff`, `RocketGirlSP2ChargeUpMaxOverride`, `RocketGirlSP2ChargeUpTypeOverride`
`Rosa1`, `Rosa2`, `Ruffs1`, `Ruffs2`, `Ruffs3`, `SN_Amber_ChargeSuper`, `SN_Amber_ProjectileSize`, `SN_AntiBoss_Shield`, `SN_AttackRange_Minus1`, `SN_Bea_ChargeSuper`
`SN_Bea_ProjectileSize`, `SN_Bea_ProjectileSpeed`, `SN_ChargeRateNerf`, `SN_ChargeSuper`, `SN_Colette_ProjectileSize`, `SN_Damage_Buff`, `SN_Finx_AreaEffect`, `SN_HP_Buff`, `SN_Juju_AreaEffect`, `SN_Juju_ChargeSuper`
`SN_Juju_ProjectileSize`, `SN_Juju_ProjectileSpeed`, `SN_SpeedUpOnAtk`, `SN_Spike_AreaEffect`, `SN_Spike_ChargeSuper`, `SN_Spike_ProjectileSize`, `SN_Spike_ProjectileSpeed`, `SN_Stella_AttackRange`, `SN_Stella_ChargeSpeed`, `SN_Stella_ChargeSuper`
`SN_Stella_EffectSize`, `SamuraiLifeSteal`, `Shade1`, `Shade2`, `ShadowdemonMinionDamage`, `ShadowdemonMinionDamageOvercharged`, `ShadowdemonMinionHealth`, `ShadowdemonMinionHealthOvercharged`, `ShamanBuddySp1`, `ShamanBuddySp2`
`ShelllyBuddySp1`, `ShelllyBuddySp2`, `Shelly1`, `Shelly2`, `Shelly3`, `SoulCollectorDamageBoostAllySp`, `SoulCollectorExplodeSoulsLoseAmmo`, `SoulCollectorHomingSoulsSpBuddy`, `SoulCollectorKnockbackSoulSpawnSoulOnHit`, `SoulCollectorSpeedAndDamageBoostAllySpBuddy`
`SpeedyBuddyAreaAdditionalStatus`, `SpeedyBuddyRewindGiveAmmo`, `SpeedyBuddyRewindHealAllies`, `SpeedyChargeUltiOnMove`, `Spike1`, `Spike2`, `Spike3`, `SpikeBuddySp1`, `SpikeSp1`, `Sprout1`
`Sprout2`, `Sprout3`, `Sprout4`, `Squeak1`, `Stu1`, `Surge1`, `Surge2`, `SwarmBarleyBottleFireL1`, `SwarmBarleyBottleFireL2`, `SwarmBarleyBottleFireL3`
`SwarmDamageBoostL1`, `SwarmDamageBoostL2`, `SwarmDamageBoostL3`, `SwarmElectroBoltFireL1`, `SwarmElectroBoltFireL2`, `SwarmElectroBoltFireL2_2`, `SwarmElectroBoltFireL3`, `SwarmElectroBoltFireL3_2`, `SwarmFireAuraTraitL1`, `SwarmFireAuraTraitL2`
`SwarmFireAuraTraitL3`, `SwarmHealthBoostL1`, `SwarmHealthBoostL2`, `SwarmHealthBoostL3`, `SwarmMeteorOverTimeLevel1`, `SwarmShootDemonicProjectileOverTimeLevel1`, `SwarmShootOtherProjectileOverTimeLevel1`, `SwarmTimeBendOverTimeLevel1`, `SwarmWhirlwindFireL1`, `SwarmWhirlwindFireL2`
`SwarmWhirlwindFireL3`, `SwarmWhirlwindProjectileOverTimeLevel1`, `Swarm_MoveSpeed_Base`, `Swarm_PickupRange_Base`, `Tara1`, `Tara2`, `Tara3`, `Tara4`, `Tick1`, `Tick2`
`Tick3`, `TrickshotDudeAddUltiPercentOnBounceHit`, `TrickshotDudeDynamicGadgetExplosionBullets`, `elPrimo1`, `elPrimo2`, `elPrimo3`

## 5. Статус-эффекты (`lookup(117, ...)`) — все 455

`ActorPlaceholderRoot`, `AlternatorDamageAura`, `AlternatorHealAura`, `AlternatorHealAuraOvercharged`, `AlternatorProjectileHeal`, `AlternatorProjectileSlowTrail`, `AlternatorProjectileSpeedTrail`, `AlternatorSlowAura`
`AlternatorSpeedAura`, `AlternatorSpeedAuraOvercharged`, `AlternatorStarPowerSpeedBoost`, `AmbusherStarPowerSpeedBoost`, `AngelicGraceCooldown`, `AngelicHot`, `AngelicWrathCooldown`, `ArcadeDamageBoostAllies`
`ArcadeDamageBoostAlliesLarger`, `ArcadePluggedInSpeedBoostAllies`, `ArcadePluggedInSpeedBoostSelf`, `ArenaBuff`, `AttacherUltiDot`, `AttractorGadgetGroundedStatus`, `AttractorProjectileMagnetStatus`, `AxeJugglerStarPowerSpeedBoost`
`BarkeepPuddleSlow`, `BarleyHitPoisonNanoPower`, `BarrelBotGadgetSlow`, `Barrelbot005AfterChargeShield`, `Barrelbot005Shield`, `Barrelbot006AfterChargeShield`, `Barrelbot006Shield`, `Barrelbot007AfterChargeShield`
`Barrelbot007Shield`, `Barrelbot008AfterChargeShield`, `Barrelbot008Shield`, `Barrelbot009AfterChargeShield`, `Barrelbot009Shield`, `Barrelbot010AfterChargeShield`, `Barrelbot010Shield`, `BarrelbotAfterChargeShield`
`BarrelbotAfterShieldOvercharged`, `BarrelbotShield`, `BarrelbotShieldOvercharged`, `BaseballDamageAreaBuddySlowStatusEffect`, `BaseballDamageAreaSlowStatusEffect`, `BaseballGadgetSkillHealStatusEffect`, `BaseballGadgetStickyAreaSlow`, `BaseballStarPowerSpeedBoost`
`BeamerProjectileSlow`, `BeeSniperAreaSlow`, `BeeSniperUltiProjectileSlow`, `BloodHuntSpeedBoost`, `BlowerStarPowerAttackProjectileSlow`, `BombHeistSafeDamageImmunity`, `BossQuizSuperChargeBuff`, `BossRaceProtection`
`BoulderStun`, `BoxDamageBuff`, `BoxHealthBuff`, `BoxShield`, `BoxSpeedBoost`, `BrawlBallDeathStun`, `BullAreaSlow`, `BullDudeBuddyTakedownShield`
`BullDudeGadget2`, `BullDudeStompGadget`, `BullGadget1`, `BullGadget1Heal`, `BullGadgetStun`, `Bulletstorm002UltiMark`, `BulletstormLastShotSlow`, `BulletstormShellPickupSpeedUp`
`BulletstormUltiMark`, `BulletstormUltiOverchargedMark`, `CactusPoppingBuddy`, `CactusPoppingBuddyStatusEffect`, `CactusUltiExplosionSlow`, `CannonGirlGadgetSpeedAndReloadBoost`, `CannonGirlOverchargedStun`, `ChesterUltiAreaSlow`
`ChronomancerGadgetProjectileStasis`, `ChronomancerTimebendBoostSelf`, `ChronomancerTimebendSpeedBoost`, `ChronomancerTimebendSpeedReduce`, `CleanseInfiniteNoVFX`, `CocoonerTrailAreaSlow`, `CollabAssassinBleed`, `CollabItemAssasinSpeedBoost`
`CollabItemDamageDealerSpeedBoost`, `CollabItemTankSpeedBoost`, `ColtOverchargedProjectileBuff`, `ColtSpeedBuddySp`, `ConductorRemoveItemShield`, `ConductorSpSlow`, `ConductorUltiShield`, `CookerGadgetDot`
`CookerGadgetHot`, `CrossBomberStarPowerSpeedBoost`, `CrowBuddySp1`, `CrowCrippleSP`, `CrowInstadotActivateEffect`, `CrowPoison`, `CrowPoisonDaggerSlow`, `CrowPoisonDragon`
`CrowPoisonFire`, `CrowPoisonGadget`, `CrowPoisonShock`, `CrowPoisonSparkle`, `CrowPoisonVirus`, `DancerRootSp`, `DaredevilSpUltiChargeRate`, `DaredevilWeaponSpeedup`
`DeadMariachiBuddySp1UltiChargeBoost`, `DeadMariachiBuddySp2Silence`, `DeadMariachiCleanseAreaStatus`, `DeadMariachiRegenAreaBuddyReloadSpeedStatus`, `Debug`, `DemonicMomentum`, `DemonicMomentum002`, `DemonicMomentum003`
`DemonicMomentum004`, `DemonicMomentumCooldown`, `DemonicRevengeCooldown`, `DemonicRitualCooldown`, `DemonicSoulCollectorCooldown`, `DemonicStatusEffectForProjectiles`, `DemonicfireCooldown`, `DiggerDrillAttackSpeedBoost`
`DiggerStarPowerSpeedBoost`, `DodgeballDeathStun`, `DomainDamageReduceSP`, `DomainForceShowSP`, `DomainInverseDamageGadget`, `DomainOnAreaBuff`, `DomainOverchargedUltiDamage`, `DracoNanoHitBurn`
`DragonRaiderMark`, `DragonRiderUltiSpeed`, `DrillerGadgetSpeedBoost`, `DrillerOverchargedUltiAreaSlow`, `DuelistShadowRealmSelfBuff`, `DuplicatorPetTooCloseCripple`, `ElectroSniperCurse`, `ElectroSniperTrapExplosionSlow`
`EmzBuddySp1`, `EmzBuddySp2`, `EmzHitPoisonNanoPower`, `EmzOverchargedPoison`, `EnragerGadgetBuddyCcImmunity`, `EnragerGadgetBuddySpeedBoost`, `EnragerUltiSpeedBoost`, `EventMomentumSpeedBoost`
`FinxTowerUntargetable`, `FireDudeFlameShieldBuddyStatus`, `FireDudePetrolFire`, `FireDudePetrolFireBubbles`, `FireDudePetrolFireDark`, `FireDudePetrolFireIce`, `FireDudePetrolFireOvercharged`, `FireDudePetrolFireTwinkles`
`FireDudePetrolSpBuddySpeed`, `FireDudePetrolSpSpill`, `FishTankGadgetAreaSlow`, `FishTankStarPowerSpeedBoost`, `FleaExtraPetDot`, `FleaPetDot`, `FleaPetHot`, `ForceShow`
`FrankBuddyShield`, `FrankBuddySp1`, `FurySlowdown`, `FutureGirlGadgetPreventHealEffect`, `FutureGirlGadgetProjectileSlow`, `FutureGirlMainAttackNoop`, `FutureGirlSP1TurretSlowEffect`, `FutureGirlTurretAreaStatusEffect`
`FutureGirlTurretAreaStatusEffectOvercharged`, `GearSpeedBoostInBush`, `GeishaStormDebuff`, `GeishaTransformInvisibility`, `GeishaTransformSpeedBoost`, `GeishaTransformed003UltiDamageMark`, `GeishaTransformed003UltiDamageMarkSp`, `GeishaTransformedUltiDamageMark`
`GeishaTransformedUltiDamageMarkOvercharged`, `GeishaTransformedUltiDamageMarkSp`, `GeishaTransformedUltiDamageMarkSpOvercharged`, `GeishaWeakSpotSlowdown`, `GenericSpeedBoost`, `GhostDeadCenterReward`, `GhostFear`, `GhostIncorporeal`
`GhostIncorporealOvercharged`, `GhostPullToCenter`, `GhostShield`, `Gladiator002Fire`, `Gladiator002FireHitReadyVfx`, `GladiatorFire`, `GladiatorFireHitReadyVfx`, `GladiatorGadgetHeal`
`GladiatorSpeedBoost`, `GunslingerDoubleShotProjectileStatusEffect`, `GunslingerStarPowerMovementSpeed`, `GusOverchargedDmgProjectile`, `GusOverchargedHealingProjectile`, `HammerDudeGadgetSkillAttractionStatusEffectBuddy`, `HammerDudeGadgetSkillNoiseCancelStatusEffect`, `HunterSurvivorDetected`
`HunterSurvivorPropHuntBotHide`, `IceDudeHypothermia`, `InsectManStarPowerWaterSpeedBoost`, `InvokDemonicPetAfterDying`, `InvokeAngelicBigPetAfterDying`, `Invulnerable`, `ItemDamageAndSpeedBoost`, `ItemSpeedBoost`
`JesterGadgetSpeedBoost`, `JesterUltiPoison`, `JetpackGirl003Levitation`, `JetpackGirl003LevitationOvercharged`, `JetpackGirlLevitation`, `JetpackGirlLevitationOvercharged`, `KatanaKidGadgetSkillFishNetStatusEffect`, `KatanaKidHide`
`KatanaKidSpeedBoostAttackMaxCharge`, `LastBreath`, `LastBreathCooldown`, `LeaperGadgetSlow`, `LeonBuddyInvisibilityStatusEffect`, `LightyearFire`, `LuchadorFire`, `LuchadorFireHyperchargePunch`
`LuchadorStarPowerShieldBuddy`, `LuchadorStarPowerSpeedBoost`, `LuchadorStarPowerSpeedBoostBuddy`, `LuchadorThrowLandDamage`, `MagicalGirlLevitation`, `MagicalGirlShieldOvercharged`, `MagicalGirlUltiAttackBuff`, `MagicalGirlUltiStatus`
`MagicalGirlUltiStatusOvercharged`, `MaisieUltiSlow`, `MarksmanArchetypeAreaSlow`, `MarksmanHitPoison_E`, `MarksmanHitPoison_L`, `MarksmanHitPoison_S`, `MarksmanHitSlowdown`, `MechaDudeBuddyGadgetHealAuraStatus`
`MechaDudeHyperchargeSlow`, `MechaDudeUltiSpawnExplosionHyperChargedStatusEffect`, `MechaVanFriendlyMegBossPowerOff`, `MechanicTurretAreaSlow`, `MeepleOverchargedPassWall`, `MeepleSuperArea`, `MegaBossDragonCrowBurn`, `MegaBossDragonCrowBurnStrong`
`MegaBossFinxStunSmash`, `MegaBossFinxTowerHeal`, `MegaBossFinxTowerTimebendSpeedReduce`, `MegaBossGhostIncorporeal`, `MegaBossInvulnerability`, `MegaBossItemDamageAndSpeedBoost`, `MegaBossMosquitoPoison`, `MegaBossSplitterTag`
`MegaBossVulnerableGen`, `MegaCactusUltiExplosionSlow`, `MegaCrowPoison`, `MegaCrowPoisonStrong`, `MegaCrowPoisonVirus`, `MegaCrowPoisonVirusStrong`, `MegaFinxTimeStopProjectileSlow`, `MegaStickyBombAreaSlow`
`MegaTickAreaSlow`, `MenderGadgetHeal`, `MenderStarPowerAllyDamageBuff`, `MenderStarPowerEnemyDamageDebuff`, `MenderUltiFear`, `MenderUltiOverchargedDamageReceiveBoost`, `MenderUltiSlow`, `MenderWeaponAllyTether`
`MenderWeaponEnemyTether`, `Morningstar002RecallSlow`, `Morningstar003RecallSlow`, `MorningstarRecallSlow`, `MorningstarSuperRoot`, `MortisBuddySp2`, `MortisGadgetSkillBatsStatusEffect`, `MortisGadgetSkillBatsStatusEffectBuddy`
`MosquitoPoison`, `MosquitoPoisonShock`, `MummyGadgetSkillAcidSprayStatusEffect`, `MummyGadgetSkillAcidSprayStatusEffectBuddy`, `MummyUltiAreaSlow`, `MutantGhostIncorporeal`, `MutantRosaForceShow`, `NanoSandstormVision`
`NinjaBuddySp1`, `NinjaUltiSpeedBoost`, `OnGadgetSpeedyUpAreaSpeedBoost`, `OnHitSpeedyUpAreaSpeedBoost`, `OnHitSpeedyUpAreaSpeedBoost_MaxNano`, `OnHitSpeedyUpAreaSpeedBoost_SamNano`, `OneHPInvulnerability`, `PercenterGadgetCharm`
`PercenterGadgetCharmNano`, `PercenterStarPowerChargeDamageReductionBase`, `PercenterStarPowerChargeDamageReductionHit`, `PlaceholderParryStatusEffect`, `PowerLevelerExtraUltiCharge`, `PowerLevelerExtraUltiChargeBuddy`, `PowerLevelerGadgetShield`, `PowerLevelerGadgetShieldBuddy`
`PowerLevelerSpeedBurstOnUltiAt2`, `PropHuntDisguise`, `Puppeteer002Poison`, `Puppeteer003Poison`, `Puppeteer004Poison`, `PuppeteerOverchargedMindcontrolShield`, `PuppeteerPoison`, `PuppeteerStarPowerTargetSpeedBoost`
`RedirecterPetUltiPoison`, `RedirecterPoisonTrailComponentStatus`, `RedirecterPoisonTrailDamageStatus`, `RedirecterProjectilePoison`, `RedirecterStarPowerCurrentHPPoison`, `RedirecterStarPowerSpawnPetOnTargetDeath`, `RedirecterUltiPoison`, `RockSpeedUpMovement`
`RockUltiDamageReduction`, `RockUltiOverchargedWallPass`, `RockUltiStarPowerImmunityCC`, `RockUltiTrailStatus`, `RockWeaponDamageBoost`, `RocketGirlGadgetSkillLandingSpeedBoost`, `RocketGirlSP2AimVisual`, `RocketGirlSp1UltiSpeedBoost`
`RogueHitBurnHold_E`, `RogueHitBurnHold_L`, `RogueHitBurnHold_S`, `RogueHitBurn_E`, `RogueHitBurn_L`, `RogueHitBurn_S`, `RollerFire`, `RollerFireIce`
`RosaGadgetBushSlow`, `RosaOverchargedUltiAreaSlow`, `SS_JetpackSlow`, `SafeInvulnerability`, `SamuraiHide`, `SamuraiShield`, `SandStormOverchargedAreaSpeedBoost`, `SandstormModifierVision`
`ShadowMushroomDot`, `ShadowMushroomHot`, `ShadowSmashMinionSpeed`, `ShadowdemonCloneBulletSlow`, `ShadowdemonSPMinionSpeed`, `ShamanPetShield`, `ShamanSp2AmmoReloadBoost`, `SharpenedAmmoBleed`
`ShelllyBuddySp2`, `ShootProjectileOnBasicAttackCooldown`, `ShotgunGirlClayPigeonsBuddyProjectileStatusEffect`, `ShotgunGirlGadgetSkillImmunityShieldBuddy`, `ShotgunGirlStarPowerUltiProjectileSlow`, `SignalStrikeReload`, `SilencerUltiOvercharged`, `SkaterGadgetJumpTaunt`
`SkaterGadgetProjectileTaunt`, `SkaterMutantTaunt`, `SkaterStarPowerSpeedBoost`, `SkaterUltiAmmoReductionSelf`, `SkaterUltiHCTaunt`, `SkaterUltiTaunt`, `SlowDownNanoPower_Damian`, `SlowDownNanoPower_Sam`
`SlowDownNanoPower_Surge`, `SlowdownModifierSpeedReduceCharacter`, `SlowdownModifierSpeedReduceProjectile`, `SnakeOilDot`, `SnakeOilGadgetDot`, `SnakeOilGadgetHot`, `SnakeOilHot`, `SoulCollectorSPAllySpeedAndDamageBuffBuddy`
`SoulCollectorStarPowerAllyDamageBuff`, `SpawnProtection`, `SpawnProtectionColt011`, `SpawnProtectionLeon010`, `SpeedBoostOnKillDemons`, `SpeedOfAnAngel`, `SpeedOfAnAngel002`, `SpeedOfAnAngel003`
`SpeedOfAnAngel004`, `SpeedOfAnAngel005`, `SpeedWhenUsingUltiAngels`, `SpeederSpeedBoost`, `SpeedyBuddyAreaShield`, `SpeedyBuddyOnHitSpeedBoost`, `SpeedyGadgetDashBuddyTimer`, `SpeedyGadgetDashShield`
`SpeedyOverchargedAreaSpeedBoost`, `SpeedyOverchargedUltiAreaSpeedBoost`, `SpeedyUltiAreaSpeedBoost`, `Splitter002Tag`, `Splitter004Tag`, `Splitter005Tag`, `SplitterComponentSpeedBoost`, `SplitterTag`
`StackerDebuffSlow`, `StackerDebuffSuper`, `StackerPetCollected`, `StackerPetStatus`, `Stalker002UltiDamageTargetCurrentHpBoost`, `Stalker003UltiDamageTargetCurrentHpBoost`, `StalkerUltiDamageTargetCurrentHpBoost`, `StalkerUltiInvisible`
`StarrNovaAmberOnHitSpeedyUpAreaSpeedBoost`, `StickyBombGadgetSlow`, `StickyBombUltiSlow`, `SuperSneakersSpeedBoost`, `SwarmCardSelectionSlow`, `SwarmCooldownTimer`, `SwarmNoEffectWaitTime3Seconds`, `SwarmNoEffectWaitTime5Seconds`
`SwarmPetrolFireL1`, `SwarmPetrolFireL2`, `SwarmPetrolFireL3`, `TntDudeGadgetSpeedBoost`, `TrailRunRubberBandSpeedBoost1`, `TrailRunRubberBandSpeedBoost2`, `TrailRunRubberBandSpeedBoost3`, `TrailRunRubberBandSpeedBoost4`
`TrailRunRubberBandSpeedBoost5`, `TrailRunRubberBandSpeedBoost6`, `TrailRunRubberBandSpeedBoost7`, `TrailRunSpeedBoostOnKill`, `TraitMoveSpeedInBush_E`, `TraitMoveSpeedInBush_Mini_E`, `TraitMoveSpeedInBush_Mini_S`, `TraitMoveSpeedInBush_Nano_Rosa`
`TraitMoveSpeedInBush_S`, `TrickShotDudeStarpowerAndNormalSpeedBoostBuddyStatus`, `TrickshotDudeProjectileBigBulletSplitBuddySlow`, `TrickshotDudeProjectileBigBulletSplitBuddySlowSmall`, `TriggerProjectileOnHittingCooldown`, `VecnaStunSmash`, `VoodooAreaSlow`, `VoodooGadgetShield`
`VoodooGadgetSpeedUp`, `VoodooPetProjectileSlow`, `WeaponThrowerUltiSpeedBuff`, `WhirlwindTrailFire`, `WhirlwindUltiSpeedBuff`, `WhirlwindUltiTrailFire`, `WrathOfAnAngelProjectileSlow`

## 6. Предметы (`lookup(18, ...)`)

`ArcadeAmmo`, `BasketBrawlHoop`, `BattleRoyaleBuff`, `BoxOfBombs`, `BoxOfMines`, `BoxOfOverchargedMines`, `BoxOfSelfDestructBombs`, `BoxPickupBomb`
`BoxPickupBoulder`, `BoxPickupDamageUp`, `BoxPickupHealthUp`, `BoxPickupShield`, `BoxPickupShuriken`, `BoxPickupSpeedUp`, `BoxPickupSpeeder`, `Bronson002Weapon`
`Bronson003Weapon`, `Bronson004Weapon`, `Bronson005Weapon`, `Bronson006Weapon`, `Bulletstorm002Shell`, `BulletstormShell`, `ButtonHold`, `ButtonPress`
`Cash`, `ClusterMine`, `ClusterOverchargedMine`, `Conductor002Sign`, `Conductor003Sign`, `Conductor004Sign`, `ConductorSign`, `ControllerArchetypeMine`
`Corpse`, `DamageAndSpeed`, `DamageAndSpeedMegaBoss`, `DogTag`, `DoorHorizontal`, `DoorVertical`, `EdgePushbackWallSegment`, `EdgePushbackWallSegmentBrawloween`
`ElectroTrap`, `EventCollectToken`, `ExtractionPoint`, `ExtractionZone`, `GladiatorHealingItem`, `GodzillaTransform`, `Gus002Soul`, `Gus003Soul`
`Gus004Soul`, `Gus005Soul`, `Gus006Soul`, `Gus007Soul`, `Healing`, `Health`, `HealthPack`, `HealthPackDougNanoPower`
`Hypercharge`, `InvasionBase`, `InvasionToken`, `KickerDudeMine`, `KickerDudeMineOC`, `LastStandCoin`, `MegaBossStickyBomb`, `MegaBossStickyBombLarge`
`MegaBossStickyBombUlti`, `MegaBossStickyBombUltiLarge`, `MegaTickMine`, `Mine`, `MineChoco`, `MineDemon`, `MineGift`, `MineHelmet`
`MineHorus`, `MineLotus`, `MineMecha`, `MineWasp`, `Money`, `Morningstar002GroundedWeapon`, `Morningstar003GroundedWeapon`, `MorningstarGroundedWeapon`
`NanoWok`, `OrbSpawner`, `Otis003Hugger`, `Otis003HuggerMine`, `Otis004Hugger`, `Otis004HuggerMine`, `Otis005Hugger`, `Otis005HuggerMine`
`Otis006Hugger`, `Otis006HuggerMine`, `Otto002Hugger`, `Otto002HuggerMine`, `OverChargedPortal`, `OverchargedBomb`, `OverchargedBoxOfBombs`, `OverchargedMine`
`PetWars`, `Piper002Bomb`, `Piper003Bomb`, `Piper004Bomb`, `Piper005Bomb`, `Piper006Bomb`, `Piper007Bomb`, `Piper008Bomb`
`Piper009Bomb`, `Piper010Bomb`, `Piper010OverchargedBomb`, `Piper011Bomb`, `PiperdefBomb`, `Point`, `Portal`, `RogueliteLCardSqueakStickyBomb`
`RuffsBuff`, `RuffsOverchargedBuff`, `SamuraiPoint`, `ScoreFlag`, `ScoreFlagHoisted`, `ScorePole`, `Scrap`, `SelfDestructBomb`
`ShadowMushroom`, `ShadowPoint`, `ShadowRealmMarker`, `SilencerHugger`, `SilencerHuggerMine`, `SilencerHuggerOC`, `SoulCollectorSoul`, `Speed`
`Spray`, `SpringBoardDown`, `SpringBoardDownLeft`, `SpringBoardDownLeft_Gale`, `SpringBoardDownRight`, `SpringBoardDownRight_Gale`, `SpringBoardDown_Gale`, `SpringBoardLeft`
`SpringBoardLeft_Gale`, `SpringBoardRight`, `SpringBoardRight_Gale`, `SpringBoardUp`, `SpringBoardUpLeft`, `SpringBoardUpLeft_Gale`, `SpringBoardUpRight`, `SpringBoardUpRight_Gale`
`SpringBoardUp_Gale`, `Sticky002Bomb`, `Sticky002BombUlti`, `Sticky003Bomb`, `Sticky003BombUlti`, `Sticky004Bomb`, `Sticky004BombUlti`, `Sticky005Bomb`
`Sticky005BombUlti`, `Sticky006Bomb`, `Sticky006BombUlti`, `Sticky007Bomb`, `Sticky007BombUlti`, `Sticky008Bomb`, `Sticky008BombUlti`, `StickyBomb`
`StickyBombOverchargedUlti`, `StickyBombUlti`, `SuperNovaTransformBeeSniper`, `SuperNovaTransformCactus`, `SuperNovaTransformChronomancer`, `SuperNovaTransformFireDude`, `SuperNovaTransformStella`, `SuperNovaTransformVoodoo`
`SupplyCrate`, `Teleport1`, `Teleport2`, `Teleport3`, `Teleport4`, `Tick002Mine`, `Tick003Mine`, `Tick004Mine`
`Tick005Mine`, `Tick006Mine`, `Tick007Mine`, `Tick009Mine`, `Tick010Mine`, `TrailWaypoint`, `TrainSpawner`, `Treasure`
`TreasureSpawner`, `Turret`, `UNODeck`, `WeaponThrowerOverchargedWeapon`, `WeaponThrowerWeapon`, `WindWall`

## 7. Скиллы (`lookup(20, ...)`) — 709 читаемых имён
Шаблон имени: `<Персонаж><Weapon|Ulti>`. Для использования: `char:useSkill(lookup(20,"ShellyUlti"), x, y, true)`.

`ActorPlaceholder`, `AlternatorUltiHeal`, `AlternatorUltiSpeed`, `AlternatorWeaponDamage`, `AlternatorWeaponHeal`, `AlternatorWeaponSlow`, `AlternatorWeaponSpeed`, `AmbusherUlti`
`AmbusherUlti2`, `AmbusherWeapon`, `ArcadeDoubleBonusSkill`, `ArcadeDoubleBonusSkillBuddy`, `ArcadeUlti`, `ArcadeWeapon`, `ArcadeWeaponOvercharged`, `ArtilleryDudeUlti`
`ArtilleryDudeWeapon`, `AssaultShotgunBonusSkillBomb`, `AssaultShotgunBonusSkillBombBuddy`, `AssaultShotgunBonusSkillCoinShower`, `AssaultShotgunBonusSkillCoinShowerBuddy`, `AssaultShotgunOverchargedWeapon`, `AssaultShotgunUlti`, `AssaultShotgunWeapon`
`AttacherUlti`, `AttacherUltiAlternate`, `AttacherWeapon`, `AttacherWeaponAlternate`, `AttacherWeaponAlternateOvercharge`, `AttractorGadgetGrounded`, `AttractorGadgetPushback`, `AttractorUlti`
`AttractorWeapon`, `AxeJugglerUlti`, `AxeJugglerWeapon`, `BarkeepUlti`, `BarkeepWeapon`, `BarrelBotUlti`, `BarrelBotWeapon`, `BarrelBotWeaponNanoPower`
`BaseballGadgetSkillHeal`, `BaseballGadgetSkillHealBuddy`, `BaseballGadgetSkillSticky`, `BaseballGadgetSkillStickyBuddy`, `BaseballOverchargedWeapon`, `BaseballUlti`, `BaseballWeapon`, `BeamerOverchargedUlti`
`BeamerUlti`, `BeamerWeapon`, `BeeSniperUlti`, `BeeSniperWeapon`, `BlackHoleUlti`, `BlackHoleWeapon`, `BlowerUlti`, `BlowerWeapon`
`BoneThrowerUlti`, `BoneThrowerWeapon`, `BoomBox_1`, `BoomBox_2`, `BoomBox_3`, `BossCharge`, `BossRaceBossChainLightning`, `BossRaceBossCharge`
`BossRaceBossRapidFire`, `BossRaceBossRockets`, `BossRapidFire`, `BossRapidFire2`, `BossRapidFire3`, `BossTownCrushAoE`, `BossTownCrushCharge`, `BowDudeGadgetSkillTotem`
`BowDudeGadgetSkillTotemBuddy`, `BowDudeOverchargedWeapon`, `BowDudeUlti`, `BowDudeWeapon`, `BrawlersMagnet_1`, `BrawlersMagnet_2`, `BrawlersMagnet_3`, `BuddyAccessoryAimSkill`
`BullDudeGadgetSkillMarkEnemy`, `BullDudeGadgetSkillMarkEnemyBuddy`, `BullDudeGadgetSkillStomp`, `BullDudeGadgetSkillStompBuddy`, `BullDudeOverchargedWeapon`, `BullDudeUlti`, `BullDudeWeapon`, `BulletstormUlti`
`BulletstormWeapon`, `BulletstormWeaponLastShot`, `CactusBonusSkillCover`, `CactusBonusSkillCoverBuddy`, `CactusBonusSkillPoppin`, `CactusBonusSkillPoppinBuddy`, `CactusOverchargedWeapon`, `CactusUlti`
`CactusWeapon`, `CannonGirlSmallUlti`, `CannonGirlSmallWeapon`, `CannonGirlUlti`, `CannonGirlWeapon`, `CannonGirlWeaponNanoPower`, `ChronomancerUlti`, `ChronomancerWeapon`
`ClusterBombDudeUlti`, `ClusterBombDudeWeapon`, `CocoonerPetUltiDummy`, `CocoonerPetWeapon`, `CocoonerUlti`, `CocoonerWeapon`, `ConductorUltiCharge`, `ConductorUltiSpawn`
`ConductorWeapon`, `ConductorWeaponOvercharged`, `ControllerUlti`, `ControllerWeapon`, `CookerUlti`, `CookerWeapon`, `CookerWeaponNanoPower`, `CrabUlti1`
`CrabUlti2`, `CrabUlti3`, `CrabWeapon1`, `CrabWeapon2`, `CrabWeapon3`, `CrossBomberUlti`, `CrossBomberWeapon`, `CrowOverchargedWeapon`
`CrowThrowPoisonDagger`, `CrowThrowPoisonDaggerBuddy`, `CrowUlti`, `CrowWeapon`, `DancerOverchargedUlti`, `DancerUlti`, `DancerWeaponDouble`, `DancerWeaponSingle`
`DancerWeaponTriple`, `DaredevilUlti`, `DaredevilUltiReturn`, `DaredevilWeapon`, `DeadMariachiUlti`, `DeadMariachiWeapon`, `DeadMariachiWeaponNanoPower`, `DeadMariachiWeaponOvercharged`
`DeadMariachi_CleanseGadgetSkill`, `DeadMariachi_CleanseGadgetSkill_Buddy`, `DiggerDrillUlti`, `DiggerDrillWeapon`, `DiggerUlti`, `DiggerWeapon`, `DomainOverchargedUlti`, `DomainUlti`
`DomainWeapon`, `DoorManUlti`, `DoorManWeapon`, `DoorManWeaponNanoPower`, `DragonRiderDragonWeapon`, `DragonRiderUlti`, `DragonRiderWeapon`, `DrillerUlti`
`DrillerWeapon`, `DuelistUlti`, `DuelistWeapon`, `DummySkillForAirDisc`, `DummySkillForBasketBrawl`, `DummySkillForCTF`, `DummySkillForChargeBall`, `DummySkillForChargePuck`
`DummySkillForDodgeBall`, `DummySkillForLaserBall`, `DummySkillForLaserBallBurning`, `DummySkillForLoveBomb`, `DummySkillForShuriken`, `DummySkillForSpeeder`, `DummyUltiSkillForBasketBrawl`, `DummyUltiSkillForCTF`
`DummyUltiSkillForChargeBall`, `DummyUltiSkillForChargePuck`, `DummyUltiSkillForDodgeBall`, `DummyUltiSkillForLaserBall`, `DummyUltiSkillForLaserBallBurning`, `DummyUltiSkillForLoveBomb`, `DuplicatorOverchargedPetWeapon`, `DuplicatorUlti`
`DuplicatorWeapon`, `ElectroSniperUlti`, `ElectroSniperWeapon`, `EnfOfLine_1`, `EnfOfLine_2`, `EnfOfLine_3`, `EnragerOverchargedWeapon`, `EnragerPull`
`EnragerPullBuddy`, `EnragerUlti`, `EnragerWeapon`, `FireDudeBonusSkillSpill`, `FireDudeBonusSkillSpillBuddy`, `FireDudeOverchargedWeapon`, `FireDudeUlti`, `FireDudeWeapon`
`FishTankUlti`, `FishTankWeapon`, `FleaPetUltiDummy`, `FleaPetWeapon`, `FleaUlti`, `FleaWeapon`, `FuryUlti`, `FuryWeapon`
`FuryWeaponSp`, `FutureGirlEscapeGadgetSkill`, `FutureGirlProjectileGadgetSkill`, `FutureGirlUlti`, `FutureGirlWeapon`, `GeishaTransformedUlti`, `GeishaTransformedWeapon`, `GeishaUlti`
`GeishaWeapon`, `GhostJump`, `GhostJumpBuddy`, `GhostUlti`, `GhostWeapon`, `GladiatorGadgetSkillAmp`, `GladiatorGadgetSkillWall`, `GladiatorUlti`
`GladiatorUltiArena`, `GladiatorWeapon`, `GladiatorWeaponFirePunch`, `GodzillaUlti`, `GodzillaWeapon1`, `GodzillaWeapon2`, `GunslingerGadgetSkillDoubleShot`, `GunslingerGadgetSkillDoubleShotBuddy`
`GunslingerGadgetSkillSilverBullet`, `GunslingerGadgetSkillSilverBulletBuddy`, `GunslingerOverchargedWeapon`, `GunslingerUlti`, `GunslingerWeapon`, `HammerDudeGadgetSkillAttraction`, `HammerDudeGadgetSkillAttractionBuddy`, `HammerDudeGadgetSkillNoiseCancel`
`HammerDudeGadgetSkillNoiseCancelBuddy`, `HammerDudeOverchargedWeapon`, `HammerDudeUlti`, `HammerDudeWeapon`, `HookUlti`, `HookWeapon`, `HookyTime_1`, `HookyTime_2`
`HookyTime_3`, `IceDudeUlti`, `IceDudeWeapon`, `InsectManChargeGadget`, `InsectManUlti`, `InsectManWeapon`, `InsectManWeaponNanoPower`, `InsectManWeaponPoison`
`InstagibWeapon`, `JesterOverchargedUlti`, `JesterUltiDamageArea`, `JesterUltiExploding`, `JesterUltiHeal`, `JesterUltiPoisoning`, `JesterUltiStunning`, `JesterWeapon`
`JetpackGirlUlti`, `JetpackGirlWeapon`, `Jetpack_1`, `Jetpack_2`, `Jetpack_3`, `KatanaKidGadgetSkillFishNet`, `KatanaKidUlti`, `KatanaKidWeaponFullChargeRanged`
`KatanaKidWeaponRanged`, `KatanaKidWeaponSlash`, `KickerDudeUlti`, `KickerDudeWeapon`, `KnightUlti`, `KnightWeapon`, `LeaperUlti`, `LeaperWeapon`
`LightyearFlightUlti`, `LightyearFlightWeapon`, `LightyearSwordUlti`, `LightyearSwordWeapon`, `LightyearUlti`, `LightyearWeapon`, `LuchadorChargeThrow`, `LuchadorChargeThrowBuddy`
`LuchadorOverchargedWeapon`, `LuchadorUlti`, `LuchadorWeapon`, `MagicalGirlBonusSkillFlyArea`, `MagicalGirlBonusSkillHealing`, `MagicalGirlBonusSkillHealingBlink`, `MagicalGirlUlti`, `MagicalGirlWeapon`
`MagicalGirlWeaponTransformed`, `MaisieUlti`, `MaisieWeapon`, `MaisieWeaponNanoPower`, `MechaDudeBigOverchargedUlti`, `MechaDudeBigOverchargedUltiBuddy`, `MechaDudeBigUlti`, `MechaDudeBigWeapon`
`MechaDudeBigWeaponBuddy`, `MechaDudeGadgetSkillSendIt`, `MechaDudeGadgetSkillSendItBuddy`, `MechaDudeUlti`, `MechaDudeWeapon`, `MechaDudeWeaponOverChargedBuddy`, `MechaVanFriendlyMegBossWeapon`, `MechaVanMeleeNinjaPull`
`MechaVanMeleeNinjaStab`, `MechaVanSniperLongRange`, `MechaVanSniperPiercing`, `MechaVanTankDash`, `MechaVanTankShortRange`, `MechanicUlti`, `MechanicWeapon`, `MeepleUlti`
`MeepleWallWeapon`, `MeepleWeapon`, `MegaBossAssaultShotgunBomb`, `MegaBossAssaultShotgunHCUlti`, `MegaBossAssaultShotgunMeleeBomb`, `MegaBossAssaultShotgunUlti`, `MegaBossAssaultShotgunWeapon`, `MegaBossAssaultShotgunWeaponForth`
`MegaBossAssaultShotgunWeaponSecond`, `MegaBossAssaultShotgunWeaponThird`, `MegaBossBlackHoleBoomerangWells`, `MegaBossBlackHoleGravityWells`, `MegaBossBlackHolePetShield`, `MegaBossBlackHolePushAway`, `MegaBossBlackHoleSpreadAttack`, `MegaBossBlackHoleUltiExplodingPet`
`MegaBossBlackHoleUltiShield`, `MegaBossBlackHoleWeapon`, `MegaBossCactusCharge`, `MegaBossCactusPet`, `MegaBossCactusPushAway`, `MegaBossCactusSecondWeapon`, `MegaBossCactusUlti`, `MegaBossCactusWeapon`
`MegaBossCrossBombPet`, `MegaBossCrossBombUlti360`, `MegaBossCrossBombWeapon360`, `MegaBossCrossBomberHCUlti`, `MegaBossCrossBomberMelee`, `MegaBossCrossBomberUlti`, `MegaBossCrossBomberWeapon`, `MegaBossCrossBomberWeaponSecond`
`MegaBossCrowPushAway`, `MegaBossCrowSecondUlti`, `MegaBossCrowSecondWeapon`, `MegaBossCrowUlti`, `MegaBossCrowUltiBack`, `MegaBossCrowWeapon`, `MegaBossDgAttackArea`, `MegaBossDgAttackCharge`
`MegaBossDgAttackPortalSpawn`, `MegaBossDgAttackProjectile`, `MegaBossDgPushAway`, `MegaBossDragonCrowChargeL3`, `MegaBossDragonCrowDefenceL2`, `MegaBossDragonCrowFire360L2`, `MegaBossDragonCrowFire360L3`, `MegaBossDragonCrowMeleeL1`
`MegaBossDragonCrowMeleeL2`, `MegaBossDragonCrowMeleeL3`, `MegaBossDragonCrowSummon`, `MegaBossDragonCrowUltiL3`, `MegaBossDragonCrowUltiSecondL3`, `MegaBossDragonCrowWeaponL1`, `MegaBossDragonCrowWeaponL2`, `MegaBossDragonCrowWeaponL3`
`MegaBossDragonCrowWeaponSecondL1`, `MegaBossDragonCrowWeaponSecondL2`, `MegaBossDragonCrowWeaponSecondL3`, `MegaBossDuoCharge`, `MegaBossDuoJump`, `MegaBossDuoQuiz`, `MegaBossDuoWeapon`, `MegaBossDuoWeapon360`
`MegaBossEmzAttack2`, `MegaBossEmzAttack3`, `MegaBossEmzAttack4`, `MegaBossEmzAttack5`, `MegaBossEmzPushAway`, `MegaBossFangAttack2`, `MegaBossFangAttack3`, `MegaBossFangAttack4`
`MegaBossFangAttack5`, `MegaBossFangPushAway`, `MegaBossFinxCharge`, `MegaBossFinxKittenWeapon`, `MegaBossFinxPushAway`, `MegaBossFinxReturnedSpawnKittens`, `MegaBossFinxReturnedSpawnTimebends`, `MegaBossFinxReturnedWeaponSkill`
`MegaBossFinxSpawnKittens`, `MegaBossFinxSpawnTimebends`, `MegaBossFinxTimeRift`, `MegaBossFinxTimeStopShots`, `MegaBossFinxTimebendSelf`, `MegaBossFinxTowerIdle`, `MegaBossFinxTowerPushAway`, `MegaBossFinxTowerStasis`
`MegaBossFinxWeaponSkill`, `MegaBossFrankAoePull`, `MegaBossFrankAttackCharge`, `MegaBossFrankAttackHammer`, `MegaBossFrankAttackHyper`, `MegaBossFrankAttackPushAway`, `MegaBossFrankAttackUlti`, `MegaBossFrankGroundSpikes`
`MegaBossFrankPetWeapon`, `MegaBossFrankSpawnAdds`, `MegaBossGhostDash`, `MegaBossGhostPushAway`, `MegaBossGhostSlap`, `MegaBossGhostSlapLarge`, `MegaBossInsectManJump`, `MegaBossInsectManPushAway`
`MegaBossInsectManUlti`, `MegaBossInsectManUltiSecond`, `MegaBossInsectManWeapon`, `MegaBossInsectManWeaponSecond`, `MegaBossKatanaKid_FishSpawner360Fish`, `MegaBossKatanaKid_FishSpawnerIdle`, `MegaBossKatanaKid_FishSpawnerPushAway`, `MegaBossMaisieBigProjectile`
`MegaBossMaisieBulletExplosions`, `MegaBossMaisieChargeBlast`, `MegaBossMaisieCreateTurrets`, `MegaBossMaisiePushAway`, `MegaBossMaisieUlt`, `MegaBossMaisieWeapon`, `MegaBossNitaDefence`, `MegaBossNitaMelee`
`MegaBossNitaSummonBruceWithNitaCustom`, `MegaBossNitaSummonSmallBear`, `MegaBossNitaWeapon`, `MegaBossPercenterPetSkill`, `MegaBossPercenterSpawnTurrent`, `MegaBossPercenterTurrentSpawnPet`, `MegaBossPercenterUlti`, `MegaBossPercenterWeapon`
`MegaBossPercenterWeapon360`, `MegaBossPercenterWeaponLarge`, `MegaBossRocketGirlChargeJump`, `MegaBossRocketGirlJump`, `MegaBossRocketGirlMatryoshka`, `MegaBossRocketGirlRocketRain`, `MegaBossRocketGirlUlti`, `MegaBossRocketGirlUltiOvercharged`
`MegaBossRocketGirlWeaponBasic`, `MegaBossRocketGirlWeaponRotatingStream`, `MegaBossRocketGirlWeaponRotatingStreamOvercharged`, `MegaBossSplitterAtk`, `MegaBossSplitterAtkPushAway`, `MegaBossSplitterCharge`, `MegaBossSplitterLegDefence`, `MegaBossSplitterSpawnRobotsShoot`
`MegaBossSplitterSpawnRobotsThrow`, `MegaBossSplitterUlti360`, `MegaBossSplitterWeapon`, `MegaBossSplitterWeaponRange`, `MegaBossStickyBombDash`, `MegaBossStickyBombUlti`, `MegaBossStickyBombUltiSecond`, `MegaBossStickyBombWeapon`
`MegaBossStickyBombWeaponSecond`, `MegaBossStickyPushAway`, `MegaBossTrickshot2Dash`, `MegaBossTrickshot2Dude360Madness`, `MegaBossTrickshot2DudeUlti`, `MegaBossTrickshot2PushAway`, `MegaBossTrickshot2UltraSuper`, `MegaBossTrickshot2Weapon`
`MegaBossTrickshot2WeaponSecond`, `MegaBossTrickshotDude360Madness`, `MegaBossTrickshotDudeUlti`, `MegaBossTrickshotPushAway`, `MegaBossTrickshotUltraSuper`, `MegaBossTrickshotWeapon`, `MegaBossTrickshotWeaponSecond`, `MegaBossVecAttackBigBlackhole`
`MegaBossVecAttackBlackholeDistance`, `MegaBossVecAttackDropClock`, `MegaBossVecAttackFreeze`, `MegaBossVecAttackRockExplosion`, `MegaBossVecAttackSlowProjectile`, `MegaBossVecPushAway`, `MegaKatanaKid360Fish`, `MegaKatanaKidHook`
`MegaKatanaKidPushAway`, `MegaKatanaKidUlti`, `MegaKatanaKidWeaponRanged`, `MegaKatanaKidWeaponSlash`, `MegaKenji360Madness`, `MegaKenjiAttackDeath`, `MegaKenjiAttackSlowProjectiles`, `MegaKenjiCharge`
`MegaKenjiPushAway`, `MegaKenjiSpawnKenji`, `MegaKenjiSpawnRobots`, `MegaTickPushAway`, `MegaTickUlti`, `MegaTickUltiLarge`, `MegaTickUltiMid`, `MegaTickWeapon`
`MegaTickWeaponSecond`, `MenderGadgetSkillDashHeal`, `MenderUlti`, `MenderWeapon`, `MinigunDudeUlti`, `MinigunDudeWeapon`, `MinigunDudeWeaponNano`, `MorningstarUlti`
`MorningstarWeapon`, `MorningstarWeaponRecall`, `MummyGadgetSkillAcidSpray`, `MummyGadgetSkillAcidSprayBuddy`, `MummyGadgetSkillFriendzoner`, `MummyGadgetSkillFriendzonerBuddy`, `MummyOverchargedWeapon`, `MummyUlti`
`MummyWeapon`, `NinjaBonusSkillInvisibleArea`, `NinjaBonusSkillInvisibleAreaBuddy`, `NinjaOverchargedWeapon`, `NinjaUlti`, `NinjaWeapon`, `PainterUlti`, `PainterWeapon`
`PercenterCharmAttack`, `PercenterCharmAttackBuddy`, `PercenterLifestealAttack`, `PercenterLifestealAttackBuddy`, `PercenterOverchargedWeapon`, `PercenterUlti`, `PercenterWeapon`, `PlaceholderSkillBlink`
`PlaceholderSkillParry`, `PowerLevelerUlti`, `PowerLevelerUltiOvercharged`, `PowerLevelerWeapon`, `PowerLevelerWeaponOverchargedBuddy`, `PuppeteerUlti`, `PuppeteerWeapon`, `RaidBossCharge`
`RaidBossCharge2`, `RaidBossCharge3`, `RaidBossCharge4`, `RaidBossRapidFire`, `RaidBossRapidFire2`, `RaidBossRapidFire3`, `RaidBossRapidFire4`, `RedirecterSnakePetUltiDummy`
`RedirecterSnakePetWeapon`, `RedirecterUlti`, `RedirecterUltiOvercharged`, `RedirecterWeapon`, `RedirecterWeaponSecondary`, `ReviverUlti`, `ReviverWeapon`, `RockGadgetJump`
`RockUlti`, `RockWeapon`, `RocketGirlGadgetSkillJump`, `RocketGirlGadgetSkillJumpBuddy`, `RocketGirlGadgetSkillMegaRocket`, `RocketGirlGadgetSkillMegaRocketBuddy`, `RocketGirlUlti`, `RocketGirlWeapon`
`RocketGirlWeaponBuddy`, `RollerUlti`, `RollerWeapon`, `RopeDudeUlti`, `RopeDudeWeapon`, `RosaUlti`, `RosaWeapon`, `RuffsUlti`
`RuffsWeapon`, `SamuraiUlti`, `SamuraiWeaponDash`, `SamuraiWeaponSlash`, `SandstormUlti`, `SandstormWeapon`, `ShadowdemonGadgetCloneBullet`, `ShadowdemonUltiCommand`
`ShadowdemonUltiSummon`, `ShadowdemonWeapon`, `ShamanOverchargedWeapon`, `ShamanUlti`, `ShamanWeapon`, `ShieldTankUlti`, `ShieldTankWeapon`, `ShotgunGirlBuddyBonusSkill`
`ShotgunGirlBuddyClayPigeons`, `ShotgunGirlClayPigeons`, `ShotgunGirlOverchargedWeapon`, `ShotgunGirlUlti`, `ShotgunGirlWeapon`, `ShotgungirlGadgetSkillReload`, `ShotgungirlGadgetSkillReloadBuddy`, `SignalStrike_1`
`SignalStrike_2`, `SignalStrike_3`, `SilencerUlti`, `SilencerWeapon`, `SkaterOverchargedUlti`, `SkaterUlti`, `SkaterWeapon`, `SnakeOilUlti`
`SnakeOilWeapon`, `SniperUlti`, `SniperWeapon`, `SniperWeaponNanoPower`, `SoulCollectorKnockbackSoul`, `SoulCollectorKnockbackSoulBuddy`, `SoulCollectorOverchargedWeapon`, `SoulCollectorUlti`
`SoulCollectorWeapon`, `SpawnerDudeUlti`, `SpawnerDudeWeapon`, `SpeedyDashBonusSkill`, `SpeedyDashBonusSkillBuddy`, `SpeedyRewindBonusSkill`, `SpeedyRewindBonusSkillBlink`, `SpeedyUlti`
`SpeedyWeapon`, `SpeedyWeaponOverchargedBuddy`, `SplitterLegsWeapon`, `SplitterUlti`, `SplitterWeapon`, `SplitterWeaponNanoPower`, `StackerGrenadeGadgetSkill`, `StackerUlti`
`StackerUltiLevel1`, `StackerUltiLevel2`, `StackerUltiLevel3`, `StackerWeapon`, `StalkerUlti`, `StalkerWeaponDash`, `StalkerWeaponJump`, `StickyBombUlti`
`StickyBombWeapon`, `SuperNovaBeeSniperUlti`, `SuperNovaBeeSniperWeapon`, `SuperNovaBeeSniperWeaponSecond`, `SuperNovaCactusUlti`, `SuperNovaCactusWeapon`, `SuperNovaChronomancerUlti`, `SuperNovaChronomancerWeapon`
`SuperNovaFireDudeUlti`, `SuperNovaFireDudeWeapon`, `SuperNovaMagicalGirlUlti`, `SuperNovaMagicalGirlWeaponTransformed`, `SuperNovaPercenterUlti`, `SuperNovaPercenterWeapon`, `SuperNovaVoodooPetWeapon`, `SuperNovaVoodooUlti`
`SuperNovaVoodooWeaponEarth`, `SuperNovaVoodooWeaponForest`, `SuperNovaVoodooWeaponWater`, `SuperSneakers_1`, `SuperSneakers_2`, `SuperSneakers_3`, `TntDudeUlti`, `TntDudeWeapon`
`TrainMode_1`, `TrainMode_2`, `TrainMode_3`, `TrickshotDudeGadgetSkillSpawnContainer`, `TrickshotDudeGadgetSkillSpawnContainerBuddy`, `TrickshotDudeGadgetSkillSplitterShot`, `TrickshotDudeGadgetSkillSplitterShotBuddy`, `TrickshotDudeUlti`
`TrickshotDudeWeapon`, `TrickshotDudeWeaponBuddyOvercharged`, `TwinsHyperUlti`, `TwinsUlti`, `TwinsUltiDummy`, `TwinsWeaponShotgun`, `TwinsWeaponThrower`, `UndertakerGadgetSkillBats`
`UndertakerGadgetSkillBatsBuddy`, `UndertakerGadgetSkillComboSpinner`, `UndertakerGadgetSkillComboSpinnerBuddy`, `UndertakerGadgetSkillReload`, `UndertakerGadgetSkillReloadBuddy`, `UndertakerOverchargedWeapon`, `UndertakerUlti`, `UndertakerWeapon`
`VoodooUlti`, `VoodooWeaponAll`, `VoodooWeaponEarth`, `VoodooWeaponForest`, `VoodooWeaponWater`, `WallyUlti`, `WallyWeapon`, `WeaponThrowerUlti`
`WeaponThrowerUlti2`, `WeaponThrowerWeapon`, `WeaponThrowerWeapon2`, `WhirlwindUlti`, `WhirlwindWeapon`

## 8. Зоны/AreaEffect (`lookup(17, ...)`) — 1386 читаемых имён
Используются в `spawnCirclingAreaEffect`, `teleport(..., srcAreaEffect, destAreaEffect, ...)`.

`AlternatorDamageAura`, `AlternatorHealAura`, `AlternatorHealAura002`, `AlternatorHealAuraOvercharged`, `AlternatorProjectileSlowTrail`, `AlternatorProjectileSpeedTrail`, `AlternatorProjectileSpeedTrail002`, `AlternatorSlowAura`
`AlternatorSpeedAura`, `AlternatorSpeedAura002`, `AlternatorSpeedAuraOvercharged`, `AlternatorSpeedFromCloseAlliesArea`, `Ambusher002Teleport`, `Ambusher002TeleportEnd`, `Ambusher002UltiExplosion`, `Ambusher003Teleport`
`Ambusher003TeleportEnd`, `Ambusher003UltiExplosion`, `Ambusher004Teleport`, `Ambusher004TeleportEnd`, `Ambusher004UltiExplosion`, `Ambusher005Teleport`, `Ambusher005TeleportEnd`, `Ambusher005UltiExplosion`
`AmbusherSuperChargeArea`, `AmbusherTeleport`, `AmbusherTeleportEnd`, `AmbusherUltiExplosion`, `AngelicAreaEffect`, `AngelicBulletAreaEffect`, `Angelo002UltiDamageArea`, `Angelo002UltiSwitchSkillArea`
`Angelo003UltiDamageArea`, `Angelo003UltiSwitchSkillArea`, `Angelo004UltiDamageArea`, `Angelo004UltiSwitchSkillArea`, `Arcade002Ulti`, `Arcade002Ulti_larger`, `Arcade003Ulti`, `Arcade003Ulti_larger`
`Arcade004Ulti`, `Arcade004Ulti_larger`, `Arcade005Ulti`, `Arcade005Ulti_larger`, `Arcade006Ulti`, `Arcade006Ulti_larger`, `Arcade007Ulti`, `Arcade007Ulti_larger`
`ArcadeDoubleGadget`, `ArcadeDoubleGadgetBuddy`, `ArcadeTeleport`, `ArtilleryArchetypeCollabBurn`, `ArtilleryArchetypeCollabCluster`, `ArtilleryArchetypeCollabExplosion`, `ArtilleryArchetypeCollabSpawnLvl1`, `ArtilleryArchetypeCollabSpawnLvl2`
`ArtilleryArchetypeCollabSpawnLvl3`, `ArtilleryDudeAccessoryExplosion`, `ArtilleryDudeOverchargedExplosion`, `ArtilleryDudeOverchargedTurretExplosion`, `ArtilleryDudeTurretExplosion`, `ArtilleryDudeUltiExplosion`, `Ash003PetExplosion`, `AssassinArchetypeExecuteAreaEffect`
`AssaultShotgunGadgetBombExplosion`, `AssaultShotgunGadgetDamageArea`, `AssaultShotgunGadgetDamageAreaBuddy`, `Attacher002Explosion`, `Attacher003Explosion`, `Attacher004Explosion`, `Attacher005Explosion`, `AttacherExplosion`
`AttacherExplosionOvercharged`, `Attacher_005_spawn`, `AttractorGadgetGroundedArea`, `AttractorGadgetPushbackArea`, `AttractorProjectileMagnetAreaActions`, `AttractorProjectileMagnetAreaStatuses`, `AutoHeal`, `BarkeepExplosion`
`BarkeepHealingArea`, `BarkeepSlowPuddle`, `BarkeepSlowPuddleSmall`, `BarkeepUltiExplosion`, `BarkeepWizardExplosion`, `BarkeepWizardUltiExplosion`, `BarleyMutationAreaEffect`, `BarleyOverchargedUlti`
`Barley_002_atk`, `Barley_002_ulti`, `Barley_004_atk`, `Barley_004_ulti`, `Barley_005_atk`, `Barley_005_ulti`, `Barley_006_atk`, `Barley_006_ulti`
`Barley_007_atk`, `Barley_007_ulti`, `Barley_008_atk`, `Barley_008_ulti`, `Barley_009_atk`, `Barley_009_ulti`, `Barley_def_atk`, `Barley_def_ulti`
`BarrelBotOverchargeChargeArea`, `BarrelBotSlowArea`, `BaseballGadgetSkillHealAreaEffect`, `BaseballGadgetSkillHealAreaEffectBuddy`, `BaseballGadgetSkillStickyAreaEffect`, `BaseballGadgetSkillStickyAreaEffectBuddy`, `BasketBallGroundIndicator`, `BasketBallRimHit`
`BasketBallThreePointArea`, `BeeSniperSlowArea`, `BeeSniperSlowAreaNanoPower`, `BelleMutantExplosion`, `BlackHoleOverchargedUltiExplosion`, `BlackHoleOverchargedUltiSuck`, `BlackHoleUltiExplosion`, `BlackHoleUltiSuck`
`Bo_003_atk_area`, `Bo_003_ulti1_area`, `Bo_004_atk_area`, `Bo_004_ulti1_area`, `Bo_005_atk_area`, `Bo_005_ulti1_area`, `Bo_005_ulti2_area`, `Bo_006_atk_area`
`Bo_006_ulti1_area`, `Bo_006_ulti2_area`, `Bo_007_atk_area`, `Bo_007_ulti1_area`, `Bo_007_ulti2_area`, `Bo_008_atk_area`, `Bo_008_ulti1_area`, `Bo_008_ulti2_area`
`Bo_009_atk_area`, `Bo_009_ulti1_area`, `Bo_009_ulti2_area`, `Bo_def_atk_area`, `Bo_def_overcharged_ulti1_area`, `Bo_def_overcharged_ulti2_area`, `Bo_def_ulti1_area`, `Bo_def_ulti2_area`
`Bo_overcharged_atk_area`, `Bonnie002GirlExplosion`, `Bonnie002SmallExplosion`, `Bonnie003GirlExplosion`, `Bonnie003SmallExplosion`, `Bonnie004GirlExplosion`, `Bonnie004SmallExplosion`, `Bonnie005GirlExplosion`
`Bonnie005SmallExplosion`, `Bonnie006GirlExplosion`, `Bonnie006SmallExplosion`, `BossRaceBossRocketBurn`, `BossRaceBossRocketExplosion`, `BossSpawn`, `BossTownCrushAoEArea`, `BowDudeExplosion`
`BowDudeSuperChargeArea`, `BowDudeSuperChargeAreaBuddy`, `BoxBombExplosion`, `BrockAttackAreaGadget`, `Brock_002_atk_area`, `Brock_002_ulti_area`, `Brock_004_atk_area`, `Brock_004_ulti_area`
`Brock_007_atk_area`, `Brock_007_ulti_area`, `Brock_008_atk_area`, `Brock_008_ulti_area`, `Brock_009_atk_area`, `Brock_009_ulti_area`, `Brock_010_atk_area`, `Brock_010_ulti_area_black`
`Brock_010_ulti_area_blue`, `Brock_010_ulti_area_pink`, `Brock_010_ulti_area_red`, `Brock_010_ulti_area_yellow`, `Brock_011_atk_area`, `Brock_011_ulti_area`, `Brock_012_atk_area`, `Brock_012_oc_atk_area`
`Brock_012_oc_ulti_area`, `Brock_012_spawn`, `Brock_012_ulti_area`, `Brock_def_Overcharged_ulti_area`, `Brock_def_atk_area`, `Brock_def_atk_area_fx_only`, `Brock_def_atk_oc_area`, `Brock_def_ulti_area`
`BullDudeStomp`, `BullDudeStompBuddy`, `BullSlowArea`, `BullSlowArea_002`, `BullSlowArea_003`, `BullSlowArea_004`, `BullSlowArea_005`, `BullSlowArea_006`
`BullSlowArea_007`, `BullSlowArea_008`, `BullSlowArea_009`, `BullSlowArea_010`, `BullSlowArea_012`, `BullStunArea`, `Bulletstorm002UltiMarkArea`, `Bulletstorm002UltiWarning`
`BulletstormAccessoryPushback`, `BulletstormUltiMarkArea`, `BulletstormUltiOverchargedMarkArea`, `BulletstormUltiOverchargedWarning`, `BulletstormUltiWarning`, `BurnMainAttack`, `BurnMainAttackAngry`, `BurnMainAttackElec`
`BurnMainAttackHacker`, `BurnMainAttackOvercharged`, `BurnMainAttackPropass`, `BurnMainAttackPropassOvercharged`, `BurnMainAttackRangerBlack`, `BurnMainAttackRangerBlue`, `BurnMainAttackRangerPink`, `BurnMainAttackRangerRed`
`BurnMainAttackRangerYellow`, `BurnMainAttackSteampunk`, `BurnMainAttackWater`, `BurnUlti`, `BushGrowArea`, `CTFHomeBase`, `CactusAccessoryExplosion`, `CactusCoverBuddy`
`CactusCoverHeal`, `CactusExplosion`, `CactusOverchargeUltiExplosion`, `CactusOverchargedExplosion`, `CactusOverchargedExplosion2`, `CactusOverchargedSpikeExplosion`, `CactusPoppingBuddy`, `CactusSpikeExplosion`
`CactusUltiExplosion`, `CannonGirlBulletExplosionOvercharged`, `CannonGirlExplosion`, `CannonGirlExplosionOvercharged`, `CannonGirlSmallExplosion`, `CashGrabSpawn`, `Chester002UltiDamageArea`, `Chester002UltiExplosion`
`Chester003UltiDamageArea`, `Chester003UltiExplosion`, `Chester004UltiDamageArea`, `Chester004UltiExplosion`, `Chester005UltiDamageArea`, `Chester005UltiExplosion`, `Chester006UltiDamageArea`, `Chester006UltiExplosion`
`ChesterOverchargedUltiBulletExplosion`, `ChesterOverchargedUltiDamageArea`, `ChesterOverchargedUltiExplosion`, `Chronomance002UltiDurationIncreasePulse`, `ChronomanceUltiDurationIncreasePulse`, `Chronomancer002UltiTimebend`, `Chronomancer003UltiTimebend`, `ChronomancerNanoPower`
`ChronomancerOverchargedUltiTimebend`, `ChronomancerTimeRewindLocation`, `ChronomancerUltiTimebend`, `ClusterBombDashMine`, `ClusterBombExplosion`, `ClusterBombExplosion2`, `ClusterBombExplosion_SB`, `ClusterBombOverchargedExplosion`
`ClusterBombOverchargedExplosion2`, `ClusterBombPetExplosion`, `ClusterBombPetOverchargedExplosion`, `CocoonerTrail`, `CollectionEventModifierSpawn`, `ColtRankedSpawn`, `Conductor002SignArea`, `Conductor002SignAreaDestroy`
`Conductor003SignArea`, `Conductor003SignAreaDestroy`, `Conductor004SignArea`, `Conductor004SignAreaDestroy`, `ConductorOverchargedArea`, `ConductorPassWallsBuddyGadgetFire`, `ConductorPoleFireBuddy`, `ConductorSignArea`
`ConductorSignAreaDestroy`, `ControllerArchetypeEnd`, `ControllerArchetypeTrail`, `ControllerOverchargedUltiExplosion`, `ControllerUltiExplosion`, `ControllerVisionArea`, `CookerOverchargedUltiArea`, `CookerOverchargedUltiExplosion`
`CookerUltiExplosion`, `CookingIngredientAdded`, `CookingScore`, `CookingSpawnIncomingDeliveryBot`, `CookingSpawnIncomingGuardBot`, `CrossBomberClusterExplosion`, `CrossBomberUltiClusterExplosion`, `CrossBomberVisionArea`
`Crow002UltiKnifes`, `Crow003UltiKnifes`, `Crow004UltiKnifes`, `Crow005UltiKnifes`, `Crow006UltiKnifes`, `Crow007UltiKnifes`, `Crow009UltiKnifes`, `Crow010UltiKnifes`
`CrowOverchargedUltiKnifes`, `CrowUltiKnifes`, `DamageBoost`, `DamageBoostPlugIn002`, `DamageBoostPlugIn003`, `DamageBoostPlugIn004`, `DamageBoostPlugIn005`, `DamageBoostPlugIn006`
`DamageBoostPlugIn007`, `DamageBoostPlugInLogic`, `DamageBoost_larger`, `Damian_002_spawn`, `DancerBlockProjectiles`, `DancerBlockProjectilesNanoPower`, `Daredevil002DamageArea`, `Daredevil002UltiDamage`
`Daredevil002UltiNoDamageEnter`, `Daredevil002UltiNoDamageLeave`, `Daredevil002UltiWarning`, `DaredevilDamageArea`, `DaredevilGadgetHide`, `DaredevilOverchargedUltiDamage`, `DaredevilOverchargedUltiWarning`, `DaredevilSuperChargeArea`
`DaredevilSuperChargeAreaGadget`, `DaredevilUltiDamage`, `DaredevilUltiNoDamageEnter`, `DaredevilUltiNoDamageLeave`, `DaredevilUltiWarning`, `DeadMariachiCleanseArea`, `DeadMariachiCleanseAreaBuddy`, `DeadMariachiMutantRegenArea`
`DeadMariachiRegenArea`, `DeadMariachiRegenAreaBuddy`, `DeadMariachiRogueliteRegenArea`, `DemonicAreaEffect`, `DemonicAreaEffectFire`, `DemonicBulletAreaEffect`, `DemonicFireAreaEffect`, `DemonicPowerAreaEffect`
`DemonicRevengeAreaEffect`, `DemonicRevengeAreaEffectExplosion`, `DemonicRevengeFireAreaEffect`, `Digger002DrillDive`, `Digger002DrillSurface`, `Digger002DrillTrail`, `Digger002ShrapnelArea`, `Digger002ShrapnelArea2`
`Digger003DrillDive`, `Digger003DrillSurface`, `Digger003DrillTrail`, `Digger003ShrapnelArea`, `Digger003ShrapnelArea2`, `DiggerDrillDive`, `DiggerDrillSurface`, `DiggerDrillTrail`
`DiggerOverchargedDrillDive`, `DiggerOverchargedDrillSurface`, `DiggerOverchargedDrillTrail`, `DiggerShrapnelArea`, `DiggerShrapnelArea2`, `DodgeballScore`, `Domain002DamageArea`, `Domain002DamageWarningArea`
`Domain002OwnedArea`, `Domain002OwnedAreaBig`, `DomainDamageArea`, `DomainDamageWarningArea`, `DomainOwnedArea`, `DomainOwnedAreaBig`, `DoorManDamageDropExplosion`, `DoorManDamageDropWarning`
`DoorManPortalArrive`, `DoorManPortalLeave`, `DoorManPortalOverchargedArrive`, `DoorManPortalOverchargedLeave`, `DrillerDamageArea`, `DrillerOverchargedUltiArea`, `DrillerRebuildEffect`, `DrillerReflectArea`
`DrillerUltiArea`, `Driller_002_atk`, `Driller_003_atk`, `Driller_003_ulti`, `Driller_004_atk`, `Driller_004_ulti`, `Driller_005_atk`, `Driller_005_ulti`
`Driller_006_atk`, `Driller_006_ulti`, `Driller_007_atk`, `Driller_007_ulti`, `Driller_008_atk`, `Driller_008_ulti`, `DuelistSuperChargeArea`, `DuplicatorDuplicateArea`
`DuplicatorSwapEffect`, `ElectroTrapExplosion`, `Emz_002_Ulti`, `Emz_003_Ulti`, `Emz_004_Ulti`, `Emz_005_Ulti`, `Emz_006_Ulti`, `Emz_007_Ulti`
`Enrager008OverchargedStarPowerDamage`, `Enrager008StarPowerDamage`, `Enrager009StarPowerDamage`, `Enrager010StarPowerDamage`, `EnragerOverchargedUlti`, `EnragerStarPowerDamage`, `EventExplosion`, `EventHealing`
`ExplodingBarrelExplosion`, `ExplodingTankDestroyEnvironment`, `ExplodingTankExplosion`, `ExplosionSpawn`, `FinxTeleport`, `FireDudeBarrelDeathPetrol`, `FireDudeOverchargedPetrolDistributionArea`, `FireDudePetrolDistributionArea`
`FireDudePetrolDistributionArea003`, `FireDudePetrolDistributionArea004`, `FireDudePetrolDistributionArea005`, `FireDudePetrolDistributionArea006`, `FireDudePetrolDistributionTrail`, `FireDudePetrolFire`, `FireDudePetrolFire002`, `FireDudePetrolFire003`
`FireDudePetrolFire004`, `FireDudePetrolFire005`, `FireDudePetrolFire006`, `FireDudePetrolFireOvercharged`, `FishTank002UltiArea`, `FishTank003UltiArea`, `FishTank004UltiArea`, `FishTankBlast`
`FishTankOnHitArea`, `FishTankOverchargedAreaEffect`, `FishTankUltiArea`, `FootPrint_Hunter`, `FootPrint_Survivor`, `FrogWizardUltiArea1`, `FrogWizardUltiArea1Overcharged`, `FrogWizardUltiArea2`
`FrogWizardUltiArea2Overcharged`, `FrogWizardUltiArea3`, `FrogWizardUltiArea3Overcharged`, `FrogWizardUltiArea3StatusEffect`, `Fury002Explosion`, `Fury002UltiArea`, `Fury002Warning`, `Fury002WarningCrit`
`FuryExplosion`, `FuryGadgetTeleport`, `FuryOverchargedUltiArea`, `FuryUltiArea`, `FuryWarning`, `FuryWarningCrit`, `FuryWarningCritLogic`, `FutureGirlGadgetAreaEffect`
`FutureGirlGadgetAreaEffectSlow`, `FutureGirlTurretArea`, `FutureGirlTurretAreaOvercharged`, `GainedAmmoEffect`, `Geisha002StormVisibility`, `Geisha002TransformedMarkExplosionSP`, `GeishaStormDamage`, `GeishaStormLoseAmmo`
`GeishaStormOverchargedCenterDamage`, `GeishaStormVisibility`, `GeishaStormVisibilityOvercharged`, `GeishaTransformEffect`, `GeishaTransformedMarkDamagedOvercharged`, `GeishaTransformedMarkExplosionSP`, `GeishaTransformedMarkExplosionSPOvercharged`, `GeishaWeakSpotAttack`
`GhostSpookyArea`, `GhostSuperChargeArea`, `Gladiator002FireExplosion`, `Gladiator002UltiArenaAreaEffectVfx`, `Gladiator002UltiArenaDestroy`, `GladiatorFire`, `GladiatorFireExplosion`, `GladiatorFireFx`
`GladiatorGadgetSkillWallArea`, `GladiatorGadgetSkillWallAreaAstronaut`, `GladiatorOverchargedUltiAreaEffect`, `GladiatorUltiArenaAreaEffect`, `GladiatorUltiArenaAreaEffectVfx`, `GladiatorUltiArenaDestroy`, `GladiatorUltiSlowAreaNanoPower`, `GraceOfAndAngelAreaEffect`
`GrayMutationArea`, `Grom002ClusterExplosion`, `Grom002UltiClusterExplosion`, `Grom003ClusterExplosion`, `Grom003UltiClusterExplosion`, `Grom004ClusterExplosion`, `Grom004UltiClusterExplosion`, `Grom005ClusterExplosion`
`Grom005UltiClusterExplosion`, `Grom006ClusterExplosion`, `Grom006UltiClusterExplosion`, `HammerDudeGadgetSkillBlockProjectilesAreaEffect`, `Hank002Blast`, `Hank003Blast`, `Hank004Blast`, `Hank005Blast`
`Heal`, `HealBoomBox`, `HealOnMove`, `HealWithAutoAttack`, `HealingSpawn`, `HealingStationHeal`, `HealingStationHeal2`, `HealingStationHeal3`
`HealingStationHeal4`, `HeistBombExplosion`, `HeistSafePushback`, `HeroSpawn`, `HookDudePushback`, `HuggerMineExplosion`, `IceDude006UltiArea`, `IceDude007UltiArea`
`IceDudeBurgerUltiArea`, `IceDudeGadgetActivationArea`, `IceDudeKingUltiArea`, `IceDudeOverchargedUltiArea`, `IceDudeOverchargedUltiAreaInvisible`, `IceDudeStonetrollUltiArea`, `IceDudeUltiArea`, `IceDudeValentineUltiArea`
`InsectManGadgetDamageArea`, `InsectManOverchargedUltiDamageArea`, `InsectManOverchargedUltiSwitchSkillArea`, `InsectManUltiDamageArea`, `InsectManUltiSwitchSkillArea`, `InvasionSpawnExplosion`, `InvasionSpawnIncoming`, `JesterUltiDamageArea`
`JesterUltiExplosion`, `JetpackGirl002UltiExplosion`, `JetpackGirl003UltiExplosion`, `JetpackGirl004UltiExplosion`, `JetpackGirl005UltiExplosion`, `JetpackGirl006UltiExplosion`, `JetpackGirl007UltiExplosion`, `JetpackGirl008UltiExplosion`
`JetpackGirl009UltiExplosion`, `JetpackGirlGadgetDamageArea`, `JetpackGirlOverchargedUltiExplosion`, `JetpackGirlUltiExplosion`, `KatanaKidUltiDamage`, `KatanaKidUltiDamageOvercharged`, `KatanaKidUltiWarning`, `KatanaKidUltiWarningOvercharged`
`KickerDudeGadgetExplosion`, `KickerDudeMineExplosion`, `KickerDudeMineExplosionOC`, `KickerDudeMineNano`, `KickerDudeMineTrail`, `KickerDudeSweepStun`, `KingOfHillArea`, `KingOfHillAreaCapture`
`KingOfHillAreaComplete`, `KingOfHillAreaGauge`, `KnightPetExplosion`, `KnightPetOverchargedExplosion`, `KnockBackReceivingDmg`, `LastBreathPushBack`, `Leaper003UltiArea`, `Leaper003UltiAreaExplosion`
`Leaper003WeaponArea`, `Leaper004UltiArea`, `Leaper004UltiAreaExplosion`, `Leaper004WeaponArea`, `Leaper005UltiArea`, `Leaper005UltiAreaExplosion`, `Leaper005WeaponArea`, `LeaperOverchargedUltiArea`
`LeaperOverchargedUltiAreaExplosion`, `LeaperUltiArea`, `LeaperUltiAreaExplosion`, `LeaperWeaponArea`, `LightyearFlightUltiExplosion`, `LightyearSwordLanding`, `LostAmmoEffect`, `LostUltiEffect`
`LoveBombExplosion`, `LoveBombSpawn`, `LuchadorMeteorBlockProjectiles`, `LuchadorMeteorBlockProjectilesBuddy`, `LuchadorMeteorExplosion`, `LuchadorMeteorExplosionPassive`, `LuchadorMeteorSpawn`, `LuchadorMeteorSpawnSmall`
`LuchadorMeteorSuperChargeBuddy`, `LuchadorSPbuddy`, `LuchadorThrowLandingDamageAreaEffect`, `MagicalGirlBonusSkillHealingBlinkEnter`, `MagicalGirlBonusSkillHealingBlinkLeave`, `MagicalGirlFlyArea`, `Maisie002UltiShockwave`, `Maisie003UltiShockwave`
`Maisie004UltiShockwave`, `Maisie005UltiShockwave`, `MaisieDashArea`, `MaisieOverchargedUltiBulletExplosion`, `MaisieOverchargedUltiShockwave`, `MaisieUltiShockwave`, `Mandy_008_spawn`, `MarksmanArchetypeSlowArea`
`Max003UltiArea`, `Max004UltiArea`, `Max005UltiArea`, `Max006UltiArea`, `Max007UltiArea`, `MechaDudeBuddyGadgetHealArea`, `MechaDudeBulletHitExplosionOvercharged`, `MechaDudeDestroyExplosion`
`MechaDudeGadgetBuddyFire`, `MechaDudeGadgetEndExplosion`, `MechaDudeReloadTowerArea`, `MechaDudeUlti002SpawnExplosion`, `MechaDudeUlti003SpawnExplosion`, `MechaDudeUlti004SpawnExplosion`, `MechaDudeUlti005SpawnExplosion`, `MechaDudeUlti006SpawnExplosion`
`MechaDudeUlti007SpawnExplosion`, `MechaDudeUlti007SpawnExplosionHyperCharged`, `MechaDudeUltiSpawnExplosion`, `MechaDudeUltiSpawnExplosionHyperCharged`, `MechaDudeUltiSpawnExplosionHyperChargedStatusArea`, `MechaVanFodderBombDeathAttack`, `MechaVanMoveArea`, `MechaVanMoveAreaCharging`
`MechanicSlowArea`, `Meeple002SuperArea`, `Meeple003SuperArea`, `MeepleOverchargedPassWallArea`, `MeepleOverchargedSuperArea`, `MeepleRageQuitArea`, `MeepleSuperArea`, `MeepleWallArea`
`MeepleWallAreaExplosion`, `MegaBossAreaIndicatorSmall`, `MegaBossAssaultShotgunBulletExplosion`, `MegaBossAssaultShotgunBulletExplosion2`, `MegaBossAssaultShotgunBulletExplosion3`, `MegaBossAssaultShotgunBulletExplosionLarge`, `MegaBossAssaultShotgunExplosionAreaDmg`, `MegaBossAssaultShotgunExplosionAreaDmgLarge`
`MegaBossAssaultShotgunExplosionWarningEffect`, `MegaBossBlackHoleBoomerangTrailExplosion`, `MegaBossBlackHoleBoomerangTrailSuck`, `MegaBossBlackHoleBoomerangTrailWarning`, `MegaBossBlackHoleGravityWellWarning`, `MegaBossBlackHolePetExplosion`, `MegaBossBlackHolePetExplosionWarning`, `MegaBossBlackHolePushBack`
`MegaBossBlackHoleUltiShieldExplosion`, `MegaBossBlackHoleUltiSuck`, `MegaBossBoomPushAwayArea`, `MegaBossCactusPushAwayArea`, `MegaBossCactusPushAwaySpike`, `MegaBossCactusSpikeExplosion`, `MegaBossClusterBombExplosion`, `MegaBossClusterBombExplosion2`
`MegaBossClusterBombPetExplosion`, `MegaBossClusterBombPetExplosionLarge`, `MegaBossClusterBombPetExplosionMid`, `MegaBossColetteChargeProjectileArea`, `MegaBossColetteProjectileExplodeArea`, `MegaBossColetteProjectileExplodeAreaSmall`, `MegaBossColetteProjectileExplodeAreaSmallDense`, `MegaBossCrossBomberAreaEffect`
`MegaBossCrossBomberAreaEffectFire`, `MegaBossCrossBomberClusterExplosion`, `MegaBossCrossBomberClusterSecondExplosion`, `MegaBossCrossBomberClusterSecondExplosion2`, `MegaBossCrossBomberUltiClusterExplosion`, `MegaBossCrowFire`, `MegaBossCrowFireExplosion`, `MegaBossCrowFireWarningEffect`
`MegaBossCrowJumpKnifes`, `MegaBossCrowJumpKnifesExplode`, `MegaBossCrowJumpKnifesPushAway`, `MegaBossCrowJumpKnifesPushAwayArea`, `MegaBossCrowJumpKnifesSmall`, `MegaBossCrowJumpKnifesSmallMore`, `MegaBossCrowMidSizeIndicator`, `MegaBossCrowPushBackL1`
`MegaBossCrowPushBackL2`, `MegaBossCrowPushBackL3`, `MegaBossCrowSwamp`, `MegaBossCrowSwampLarge`, `MegaBossCrowSwampStatus`, `MegaBossCrowSwampStatusLarge`, `MegaBossCrowUltiIndicator`, `MegaBossDgDamageArea`
`MegaBossDgPushBack`, `MegaBossDgSpawnBullets`, `MegaBossDragonCrowUltiKnifesL1`, `MegaBossDragonCrowUltiKnifesL3`, `MegaBossDragonCrowUltiKnifesSmallL3`, `MegaBossDuoDamageArea`, `MegaBossDuoDamageAreaBulletLarge`, `MegaBossDuoDamageAreaBulletSmall`
`MegaBossDuoQuizCorrectAnswerEffect`, `MegaBossDuoQuizOutsideEffect`, `MegaBossDuoQuizWrongAnswerEffect`, `MegaBossDuoQuizZoneA`, `MegaBossDuoQuizZoneB`, `MegaBossDuoQuizZoneC`, `MegaBossFinxAddTrigger`, `MegaBossFinxAddWarning`
`MegaBossFinxStasisAreaDamage`, `MegaBossFinxStasisAreaStun`, `MegaBossFinxStasisAreaWarning`, `MegaBossFinxTimeRiftBulletExplosion`, `MegaBossFinxTimeStopBulletExplosion`, `MegaBossFinxTimebend`, `MegaBossFinxTimebendSelf`, `MegaBossFinxTowerStasisAreaDamage`
`MegaBossFinxTowerStasisAreaStun`, `MegaBossFinxTowerStasisAreaWarning`, `MegaBossFinxTowerTimebend`, `MegaBossFinxTrailArea`, `MegaBossFrankAddTrigger`, `MegaBossFrankAddWarning`, `MegaBossFrankFireArea`, `MegaBossFrankGroundSpike`
`MegaBossFrankGroundWarning`, `MegaBossFrankPull`, `MegaBossFrankPullWarning`, `MegaBossFrankStunArea`, `MegaBossFrankStunIndicator`, `MegaBossGhostBulletExplode`, `MegaBossGhostPushBack`, `MegaBossGhostSlap`
`MegaBossGhostSlapLarge`, `MegaBossGhostSpookyArea`, `MegaBossIndicatorLarge`, `MegaBossInsectManBulletExplosion`, `MegaBossInsectManPushAway`, `MegaBossInsectManUltiDamageArea`, `MegaBossInsectManUltiDamageAreaLarge`, `MegaBossKatanaKid_FishSpawner360FishExplosion`
`MegaBossKatanaKid_FishSpawner360FishExplosion2`, `MegaBossMaisieBulletExplosion`, `MegaBossMaisieExplosionAreaDmg`, `MegaBossMaisieExplosionWarningEffect`, `MegaBossMaisieShockwaveBulletExplosion`, `MegaBossMaisieUltiShockwave`, `MegaBossNitaMelee`, `MegaBossOverchargeStickyBombClusterExplosion`
`MegaBossOverchargedCrossBomberUltiClusterExplosion`, `MegaBossOverchargedCrossBomberUltiClusterExplosion2`, `MegaBossOverchargedCrossBomberUltiClusterExplosion3`, `MegaBossRicoMoveBullet1`, `MegaBossRicoMoveBullet2`, `MegaBossRicoMoveBullet3`, `MegaBossRocketGirlBasicProjectileArea`, `MegaBossRocketGirlJumpExplosion`
`MegaBossRocketGirlJumpExplosionWarning`, `MegaBossRocketGirlRainWarning`, `MegaBossRocketGirlRocketExplosion`, `MegaBossRocketGirlTrailArea`, `MegaBossRocketGirlUltiArea`, `MegaBossRocketGirlsRainArea`, `MegaBossStickyBombClusterExplosion`, `MegaBossStickyBombExplosion`
`MegaBossStickyBombExplosionLarge`, `MegaBossStickyBombSlowArea`, `MegaBossStickyBombSlowAreaLarge`, `MegaBossStickyBombSlowAreaSmall`, `MegaBossStickyBombSlowAreaTiny`, `MegaBossStickyBombUltiExplosion`, `MegaBossStickyBombUltiExplosionLarge`, `MegaBossTrickShotDestroyArea`
`MegaBossVecBigBlackhole`, `MegaBossVecBigBlackholeEffect`, `MegaBossVecBlackholeDistanceArea`, `MegaBossVecBlackholeDistanceAreaDmg`, `MegaBossVecBlackholeDistanceAreaEffect`, `MegaBossVecBlackholeDistanceAreaStun`, `MegaBossVecClockExplosion`, `MegaBossVecClockSpawn`
`MegaBossVecFreezeArea`, `MegaBossVecFreezeExplosion`, `MegaBossVecPushBack`, `MegaBossVecRockExplosion`, `MegaBossVecRockExplosionBullets`, `MegaBossVecRockExplosionDamage`, `MegaBossVecTeleport`, `MegaBossVecTeleportEnd`
`MegaBossWarning360`, `MegaCactusExplosion`, `MegaCactusSpikeExplosion`, `MegaCactusSpikeExplosionSecond`, `MegaCactusSpikeExplosionSecondChain1`, `MegaCactusSpikeExplosionSecondChain2`, `MegaCactusUltiExplosion`, `MegaCactusUltiExplosionLarge`
`MegaKatanaKid360FishExplosion`, `MegaKatanaKidDashTrail`, `MegaKatanaKidFishExplosion`, `MegaKatanaKidPushBack`, `MegaKatanaKidUltiDamage`, `MegaKatanaKidUltiIndicator`, `MegaKenjiBulletExplosion360`, `MegaKenjiBulletExplosion3602`
`MegaKenjiBulletExplosion3603`, `MegaKenjiBulletExplosion3604`, `MegaKenjiBulletExplosionPet`, `MegaKenjiPushBack`, `MegaSplitterLegs360`, `MegaSplitterLegs360Chain1`, `MegaSplitterLegs360Chain2`, `MegaSplitterLegsDamageArea`
`MegaSplitterLegsDamageAreaPushAway`, `MegaStickyBombPushAwayArea`, `MegaStickyBombPushAwayExplosion`, `MegaStickyBombPushAwayExplosionSmall`, `MegaStickyBombPushAwayExplosionTiny`, `MegaTickMeteorite`, `MegaTickMeteoriteExplosion`, `MegaTickPushAwayArea`
`MegaTickPushAwayBoom`, `MegaTickSlowArea`, `MegaTrickshotDude2_360Madness`, `MegaTrickshotDude2_360Madness2`, `MegaTrickshotDude2_360Madness3`, `MegaTrickshotDude2_360Madness4`, `MegaTrickshotDude2_360PushAwayArea`, `MegaTrickshotDude2_360PushAwayBullet`
`MegaTrickshotDude360Madness`, `MegaTrickshotDude360Madness2`, `MegaTrickshotDude360Madness3`, `MegaTrickshotDude360Madness4`, `MegaTrickshotDude360PushAwayArea`, `MegaTrickshotDude360PushAwayBullet`, `MenderGadgetSkillHealArea`, `Mico_002_UltiArea`
`Mico_002_UltiAreaExplosion`, `Mico_002_WeaponArea`, `Mike012OverchargedUltiClusterBombs`, `Mike_005_ulti_explosion`, `Mike_007_explosion`, `Mike_007_ulti_explosion`, `Mike_008_explosion`, `Mike_008_ulti_explosion`
`Mike_009_explosion`, `Mike_009_ulti_explosion`, `Mike_010_explosion`, `Mike_010_ulti_explosion`, `Mike_011_explosion`, `Mike_011_ulti_explosion`, `Mike_012_explosion`, `Mike_012_oc_cluster_explosion`
`Mike_012_oc_explosion`, `Mike_012_oc_spawn`, `Mike_012_oc_ulti_explosion`, `Mike_012_ulti_explosion`, `MineExplosion`, `MinigunDudeTowerBurstHeal`, `MinigunOverchargedHealingStationHeal`, `MinigunOverchargedInstantHeal`
`MinionSpawnArea`, `MinionSpawnCapture`, `MinionSpawnComplete`, `MinionSpawnGauge`, `MinionSpawnKaijuGauge`, `Morningstar002UltiArea1`, `Morningstar002UltiArea2`, `Morningstar002UltiArea3`
`Morningstar003UltiArea1`, `Morningstar003UltiArea2`, `Morningstar003UltiArea3`, `MorningstarFireGadgetArea`, `MorningstarIceGadgetArea`, `MorningstarUltiArea1`, `MorningstarUltiArea1Overcharged`, `MorningstarUltiArea1SP`
`MorningstarUltiArea2`, `MorningstarUltiArea2Overcharged`, `MorningstarUltiArea2SP`, `MorningstarUltiArea3`, `MorningstarUltiArea3Overcharged`, `MorningstarUltiArea3SP`, `MorningstarUltiArea3StatusEffect`, `Mortis008OverchargedBulletSpawner`
`MortisOverchargedBulletSpawner`, `MrpMutationArea`, `Mrp_003_atk_explosion`, `Mrp_004_atk_explosion`, `Mrp_005_atk_explosion`, `Mrp_006_atk_explosion`, `Mrp_007_atk_explosion`, `Mspawn`
`MummyAccessoryPushback`, `MummyOverchargedUltiArea`, `MummyOverchargedUltiAreaPushBack`, `MummyOverchargedUltiBulletExplosion`, `MummyUltiArea`, `MutantBushGrowArea`, `Nani004UltiExplosion`, `Nani005UltiExplosion`
`Nani006UltiExplosion`, `Nani007UltiExplosion`, `Nani008UltiExplosion`, `NanoColetteChargeProjectileArea`, `NinjaBuddyGadgetTeleportEffect`, `NinjaInvisibleArea`, `NinjaInvisibleAreaBuddy`, `Ninja_010_spawn`
`OnGadgetSpeedyUpArea`, `OnHitSpeedyUpArea`, `OnHitSpeedyUpAreaEffectOnly`, `OnHitSpeedyUpArea_MaxNanoPower`, `OnHitSpeedyUpArea_SamNanoPower`, `OnHitSpeedyUpArea_StarNovaAmber`, `OnKillHealArea`, `OneHPShieldPushback`
`Otto002BigProjectileExplosion`, `Otto002MineExplosion`, `OutOfLineArea`, `OutOfLineArea_lvl3`, `OverchargedCrossBomberUltiClusterExplosion`, `OverchargedCrossBomberUltiClusterExplosion2`, `PaintBallSplash`, `PaintBallSplash_big`
`Painter002AreaEffect`, `Painter002AreaEffectEnd`, `Painter002AreaExplosion`, `Painter003AreaEffect`, `Painter003AreaEffectEnd`, `Painter003AreaExplosion`, `Painter004AreaEffect`, `Painter004AreaEffectEnd`
`Painter004AreaExplosion`, `Painter005AreaEffect`, `Painter005AreaEffectEnd`, `Painter005AreaExplosion`, `PainterAccessoryArea`, `PainterAreaEffect`, `PainterAreaEffectEnd`, `PainterAreaEffectEndMutant`
`PainterAreaEffectEndOvercharged`, `PainterAreaEffectMutant`, `PainterAreaEffectOvercharged`, `PainterAreaExplosion`, `PayloadMoveArea`, `PayloadMoveAreaPushed`, `PayloadMoveAreaSlowed`, `PayloadSingleMoveArea`
`Pearl002UltiExplosion`, `Pearl003UltiExplosion`, `Pearl004UltiExplosion_k2`, `PengulaExplosion`, `Penny005TurretExplosion`, `Penny006TurretExplosion`, `Penny007TurretExplosion`, `Penny008BurnUlti`
`Penny008TurretExplosion`, `Penny009BurnUlti`, `Penny009TurretExplosion`, `PercenterAreaEffectMutant`, `Piper_003_ulti`, `Piper_004_ulti`, `Piper_005_ulti`, `Piper_006_ulti`
`Piper_007_ulti`, `Piper_008_ulti`, `Piper_009_ulti`, `Piper_010_hc_ulti`, `Piper_010_ulti`, `Piper_011_ulti`, `Piper_def_ulti`, `PoisonBarrelExplosion`
`PowerLevelerOverchargedUltiProjectiles`, `PowerLevelerSlowAreaNanoPower`, `PowerupSpawn`, `PullRopeStun`, `PullRopeStun002`, `PullRopeStun006`, `PullRopeStun007`, `PullRopeStun007Overcharge`
`PullRopeStun008`, `PullRopeStun009`, `PullRopeStun010`, `PullRopeStunOvercharge`, `Puppeteer002Dive`, `Puppeteer002Poison`, `Puppeteer002PoisonAlternative`, `Puppeteer003Dive`
`Puppeteer003Poison`, `Puppeteer003PoisonAlternative`, `Puppeteer004Dive`, `Puppeteer004Poison`, `Puppeteer004PoisonAlternative`, `PuppeteerDive`, `PuppeteerPoison`, `PuppeteerPoisonAlternative`
`PushAwayAreaNanoPower`, `PushbackBoomBox`, `PushbackBoomBoxLvL3`, `RaidBossExplosion`, `RaidBossExplosionSpawn`, `RaidBossRocketBurn`, `Redirecter002PetUltiExplosion`, `Redirecter002UltiExplosion`
`RedirecterCocoonExplosion`, `RedirecterOverchargedSnakePetPoisonTrailArea`, `RedirecterPetUltiExplosion`, `RedirecterPetUltiExplosionOvercharged`, `RedirecterPoisonTrailArea`, `RedirecterUltiExplosion`, `Reviver002DamageArea`, `Reviver003DamageArea`
`Reviver004DamageArea`, `Reviver005DamageArea`, `ReviverDamageArea`, `ReviverDamageAreaDoubleDamage`, `ReviverDamageAreaDoubleHeal`, `RoboWarsBaseAreaIndicator`, `RoboWarsBaseExplosion`, `RoboWarsBoxSpawn`
`RockGadgetJumpArea`, `RockUltiTrail`, `RocketGirlExplosion`, `RocketGirlGadgetJumpArea`, `RocketGirlGadgetJumpAreaBuddy`, `RocketGirlGadgetSkillMegaRocketEndExplosion`, `RocketGirlUltiExplosion`, `RocketJumpExplosion`
`RoguelikeShieldAreaEffect_E`, `RoguelikeShieldAreaEffect_L`, `RoguelikeShieldAreaEffect_S`, `RogueliteDancerBlockProjectiles`, `RogueliteLCardBombExplosion`, `RogueliteLCardSlowArea`, `RogueliteLCardSqueak`, `Roller002Fire`
`Roller003Fire`, `Roller004Fire`, `Roller005Fire`, `Roller006Fire`, `RollerFire`, `RollerMutationArea`, `RollerOverchargedFire`, `RopeDudeSuperChargeArea`
`RopeDudeSuperChargeAreaLarge`, `RosaOverchargedUltiArea`, `Ruffs002SupplySpawn`, `Ruffs003SupplySpawn`, `Ruffs004SupplyExplosion`, `Ruffs004SupplySpawn`, `Ruffs005SupplyExplosion`, `Ruffs005SupplySpawn`
`Ruffs006SupplyExplosion`, `Ruffs006SupplySpawn`, `Ruffs007SupplyExplosion`, `Ruffs007SupplySpawn`, `RuffsAirStrikeExplosion`, `RuffsAirStrikeSpawn`, `RuffsIncreaseHealth`, `RuffsOverchargedSupplyExplosion`
`RuffsOverchargedSupplySpawn`, `RuffsSupplyExplosion`, `RuffsSupplySpawn`, `Samurai002CrossSlashArea`, `Samurai003CrossSlashArea`, `Samurai003OverchargedCrossSlashArea`, `Samurai003OverchargedPullInArea`, `Samurai004CrossSlashArea`
`SamuraiCrossSlashArea`, `SamuraiItemPickup`, `SamuraiOverchargedCrossSlashArea`, `SamuraiOverchargedPullInArea`, `SamuraiSmashSpawn`, `SamuraiSmashSpawnIncoming`, `SamuraiSmashSpawnIncomingBoss`, `SamuraiSpawnExplosion`
`SandStormOverchargedUltiArea`, `SandStormOverchargedUltiAreaSpeedBuff`, `SandStormOverchargedUltiSilenceArea`, `SandstormModifierSandstorm`, `SandyNanoSandstorm`, `Sandy_002_ulti`, `Sandy_003_ulti`, `Sandy_004_ulti`
`Sandy_005_ulti`, `Sandy_006_ulti`, `Sandy_007_ulti`, `Sandy_def_ulti`, `SbcontrollerAreaDestroy`, `SelfDestructExplosion`, `ShadowdemonIndirectExplosion`, `ShadowdemonMinionSummon`
`ShadowdemonMinionTarget`, `ShadowdemonTeleportGadgetEnter`, `ShadowdemonTeleportGadgetLeave`, `ShamanBearSlam`, `ShellyBuddySPBurnArea`, `ShieldEffectDamageDeduction`, `ShieldEffectInvulnerable`, `ShieldTankHeal`
`ShieldTankSuperChargeArea`, `ShotgunGirl_010_spawn`, `SilencerBigProjectileExplosion`, `Skater002UltiLanding`, `Skater002UltiTaunt`, `Skater003UltiLanding`, `Skater003UltiTaunt`, `Skater004UltiLanding`
`Skater004UltiTaunt`, `SkaterGadgetTaunt`, `SkaterUltiLanding`, `SkaterUltiLandingOvercharged`, `SkaterUltiTaunt`, `SkaterUltiTauntOvercharged`, `SnakeOilHyperUltiBulletExplosion`, `SnakeOilRingMasterExplosion`
`SnakeOilSubwaySufersExplosion`, `SnakeOilUltiExplosion`, `SnakeOilUltiHyperExplosion`, `SnakeOilVillainExplosion`, `SnakeOilWindStockExplosion`, `SnakeOilWizardUltiExplosion`, `SniperBombExplosion`, `SniperOverchargedBombExplosion`
`SniperOverchargedLanding`, `SoulCollectorOverchargedAreaEffect`, `SoulCollectorOverchargedPushback`, `SoulCollectorPushback`, `SoulCollectorSoulExplosion`, `SoulCollectorSoulExplosionLoseAmmo`, `SpawnerDudeExplosion`, `SpawnerDudeOverchargedExplosion`
`SpeedBoost`, `SpeederDestroyEnvironment`, `SpeederExplosion`, `SpeedyOverchargedArea`, `SpeedyOverchargedArea2`, `SpeedyOverchargedBuddyWeaponArea`, `SpeedyRewindAllyHealArea`, `SpeedyRewindArea`
`SpeedyRewindTeleport`, `SpeedyUltiArea`, `SpeedyUltiOverchargedArea`, `SpikeExplosionLowHealth`, `Spike_002_atk1_explosion`, `Spike_002_atk2`, `Spike_002_ulti_explosion`, `Spike_003_atk1_explosion`
`Spike_003_atk2`, `Spike_003_ulti_explosion`, `Spike_004_atk1_explosion`, `Spike_004_atk2`, `Spike_004_ulti_explosion`, `Spike_005_atk1_explosion`, `Spike_005_atk2`, `Spike_005_ulti_explosion`
`Spike_006_atk1_explosion`, `Spike_006_atk2`, `Spike_006_ulti_explosion`, `Spike_007_atk1_explosion`, `Spike_007_atk2`, `Spike_007_ulti_explosion`, `Spike_008_atk1_explosion`, `Spike_008_atk2`
`Spike_008_ulti_explosion`, `Spike_009_atk1_explosion`, `Spike_009_atk2`, `Spike_009_ulti_explosion`, `Spike_010_atk1_explosion`, `Spike_010_atk2`, `Spike_010_ulti_explosion`, `Splitter002LegsDamageArea`
`Splitter004LegsDamageArea`, `Splitter005LegsDamageArea`, `SplitterLegsDamageArea`, `SplitterTagExplosion`, `Sprout_002_atk`, `Sprout_002_sp1`, `Sprout_002_ulti`, `Sprout_003_atk`
`Sprout_003_chroma_ulti`, `Sprout_003_sp1`, `Sprout_003_ulti`, `Sprout_004_atk`, `Sprout_004_sp`, `Sprout_004_ulti`, `Sprout_005_atk`, `Sprout_005_sp`
`Sprout_005_ulti`, `Sprout_006_atk`, `Sprout_006_sp`, `Sprout_006_ulti`, `Sprout_007_atk`, `Sprout_007_sp`, `Sprout_007_ulti`, `Squeak002ClusterExplosion`
`Squeak003BombExplosion`, `Squeak003ClusterExplosion`, `Squeak003UltiExplosion`, `Squeak004BombExplosion`, `Squeak004ClusterExplosion`, `Squeak004UltiExplosion`, `Squeak005BombExplosion`, `Squeak005ClusterExplosion`
`Squeak005UltiExplosion`, `Squeak006BombExplosion`, `Squeak006ClusterExplosion`, `Squeak006UltiExplosion`, `Squeak007BombExplosion`, `Squeak007ClusterExplosion`, `Squeak007UltiExplosion`, `Squeak008BombExplosion`
`Squeak008ClusterExplosion`, `Squeak008UltiExplosion`, `StackerAmmoSpawnArea`, `StackerGadgetActionArea`, `StackerGadgetDamageArea`, `StackerGadgetPetAutocollectArea`, `Stalker002WeaponJumpArea`, `Stalker003WeaponJumpArea`
`StalkerWeaponJumpArea`, `StarNovaPickupSpawnIndicator_Amber`, `StarNovaPickupSpawnIndicator_Bea`, `StarNovaPickupSpawnIndicator_Juju`, `StarNovaPickupSpawnIndicator_Spike`, `StarNovaPickupSpawnIndicator_Stella`, `StarNovaPickupSpawn_Amber`, `StarNovaPickupSpawn_Bea`
`StarNovaPickupSpawn_Fast_Amber`, `StarNovaPickupSpawn_Fast_Bea`, `StarNovaPickupSpawn_Fast_Juju`, `StarNovaPickupSpawn_Fast_Spike`, `StarNovaPickupSpawn_Fast_Stella`, `StarNovaPickupSpawn_Juju`, `StarNovaPickupSpawn_Spike`, `StarNovaPickupSpawn_Stella`
`StickyBombClusterExplosion`, `StickyBombExplosion`, `StickyBombMutantClusterExplosion`, `StickyBombOverchargedClusterExplosion`, `StickyBombOverchargedUltiExplosion`, `StickyBombUltiExplosion`, `StickyBombVisionArea`, `SubwayJetpackDamage`
`SubwayJetpackSlow`, `SubwayTrainRushProjectileSpeedTrail`, `SuperNovaCactusExplosion`, `SuperNovaCactusSpikeExplosion`, `SuperNovaCactusSpikeExplosionMini`, `SuperNovaCactusUltiExplosion`, `SuperNovaCactusUltiSpikeExplosion`, `SuperNovaVoodooAttackEarthLarge`
`SuperNovaVoodooAttackEarthMid`, `SuperNovaVoodooAttackEarthSmall`, `SuperNovaVoodooAttackForestLarge`, `SuperNovaVoodooAttackForestMid`, `SuperNovaVoodooAttackForestSmall`, `SuperNovaVoodooAttackWaterLarge`, `SuperNovaVoodooAttackWaterMid`, `SuperNovaVoodooAttackWaterSmall`
`SuperNovaVoodooSlowDebuffLarge`, `SuperNovaVoodooSlowDebuffMid`, `SuperNovaVoodooSlowDebuffSmall`, `SuperSneakersSpeed`, `SupportArchetypeHeal`, `SupportArchetypeSpawn`, `SwarmCardSelectionSlowArea`, `SwarmFireAuraL1`
`SwarmFireAuraL2`, `SwarmFireAuraL3`, `TankBushGrowArea`, `TankBushGrowAreaLarge`, `Tara004UltiExplosion`, `Tara004UltiSuck`, `Tara005UltiSuck`, `Tara006UltiSuck`
`Tara007UltiSuck`, `Tara008UltiSuck`, `TeleportTileArrive`, `TeleportTileLeave`, `Tick002Explosion`, `Tick002Explosion2`, `Tick003Explosion`, `Tick003Explosion2`
`Tick004Explosion`, `Tick004Explosion2`, `Tick005Explosion`, `Tick005Explosion2`, `Tick006Explosion`, `Tick006Explosion2`, `Tick006PetExplosion`, `Tick007Explosion`
`Tick007Explosion2`, `Tick007PetExplosion`, `Tick009Explosion`, `Tick009Explosion2`, `Tick009PetExplosion`, `Tick010Explosion`, `Tick010Explosion2`, `Tick010PetExplosion`
`TickGadgetExplosion`, `TntDudeAttackNanoPowerBombs`, `TntDudeExplosion`, `TntDudeOverchargedExplosion`, `TntDudeOverchargedUltiClusterBombs`, `TntDudeOverchargedUltiClusterExplosion`, `TntDudeOverchargedUltiExplosion`, `TntDudeUltiExplosion`
`TrailRunWaypointActivation`, `TrailRunWin`, `TrainModeAreaEffect`, `TrickshotDudeAccessoryExplosion`, `TrickshotDudeBulletBouncerAreaEffect`, `TrickshotDudeBulletBouncerAreaEffectBuddy`, `TrickshotDudeNanoExplosion`, `TrickshotDudeNanoSuperExplosion`
`TrophyArea`, `Twins002ThrowerExplosion`, `Twins002ThrowerExplosion2`, `Twins003ThrowerExplosion`, `Twins003ThrowerExplosion2`, `Twins004ThrowerExplosion`, `Twins004ThrowerExplosion2`, `TwinsThrowerExplosion`
`TwinsThrowerExplosion2`, `TwinsThrowerMutantExplosion`, `UndertagerGadgetSkillBatsAreaEffect`, `UndertakerGadgetSkillComboSpinnerAreaExplosion`, `UndertakerGadgetSkillComboSpinnerBuddyAreaExplosion`, `UndertakerSwingDamage`, `UnoCardSpawn`, `UnoDrawTwo`
`UnoScore`, `UnoSkip`, `VolleyBallDistanceIndicator`, `VolleyBallHit`, `VolleyBallTarget`, `VolleyBallTargetOccupied`, `Voodoo002AttackEarth`, `Voodoo002AttackForest`
`Voodoo002AttackWater`, `Voodoo003AttackEarth`, `Voodoo003AttackForest`, `Voodoo003AttackWater`, `VoodooAttackAll`, `VoodooAttackEarth`, `VoodooAttackForest`, `VoodooAttackWater`
`VoodooSlowDebuff`, `WallyExplosion`, `WallyExplosionBig`, `WallyOverchargedUltiArea`, `WallyOverchargedUltiWallDamageArea`, `WallyUltiArea`, `WeaponThroweChargeArea`, `WeaponThrowerExplosion`
`WeaponThrowerPullArea`, `WhirlwindOverchargedAreaEffect`, `WhirlwindTrail`, `WrathOfAnAngelAreaEffect`, `amber_006_spawn`, `crow_010_spawn`, `gray_005_spawn`, `lou_007_spawn`
`mecha_007_spawn`, `penny007BurnUlti`

## 9. Снаряды (`lookup(6, ...)`) — 2070 читаемых имён
`ActorPlaceholderProjectile`, `Alternator002HealProjectile`, `Alternator002SpeedProjectile`, `AlternatorDamageProjectile`, `AlternatorHealProjectile`, `AlternatorSlowProjectile`, `AlternatorSpeedProjectile`, `Ambusher002Projectile`
`Ambusher002UltiProjectile`, `Ambusher002UltiProjectile2`, `Ambusher003Projectile`, `Ambusher003UltiProjectile`, `Ambusher003UltiProjectile2`, `Ambusher004Projectile`, `Ambusher004UltiProjectile`, `Ambusher004UltiProjectile2`
`Ambusher005Projectile`, `Ambusher005UltiProjectile`, `Ambusher005UltiProjectile2`, `AmbusherOverchargedUltiProjectile`, `AmbusherProjectile`, `AmbusherUltiProjectile`, `AmbusherUltiProjectile2`, `AngelicProjectile`
`Angelo002Projectile`, `Angelo002ProjectilePoison`, `Angelo003Projectile`, `Angelo003ProjectilePoison`, `Angelo004Projectile`, `Angelo004ProjectilePoison`, `Arcade002Projectile`, `Arcade002UltiProjectile`
`Arcade003Projectile`, `Arcade003UltiProjectile`, `Arcade004Projectile`, `Arcade004UltiProjectile`, `Arcade005Projectile`, `Arcade005UltiProjectile`, `Arcade006Projectile`, `Arcade006UltiProjectile`
`Arcade007Projectile`, `Arcade007UltiProjectile`, `ArcadeDoubleBonusSkillBuddyProjectile`, `ArcadeDoubleBonusSkillBuddyProjectile2`, `ArcadeDoubleBonusSkillBuddyProjectile3`, `ArcadeDoubleBonusSkillProjectile`, `ArcadeItemDispenserProjectile`, `ArcadeOverchargedBuddyProjectile`
`ArcadeOverchargedTurretProjectile`, `ArcadeProjectile`, `ArcadeStarPowerProjectileAllies`, `ArcadeStarPowerProjectileSelf`, `ArcadeUltiOverchargedProjectile`, `ArcadeUltiProjectile`, `ArenaBaseProjectile`, `ArenaXPProjectile`
`ArtilleryArchetypeCollabClusterProjectile`, `ArtilleryDudeOverchargedTurretProjectile`, `ArtilleryDudeOverchargedUltiProjectile`, `ArtilleryDudeProjectile`, `ArtilleryDudeProjectile2`, `ArtilleryDudeTurretProjectile`, `ArtilleryDudeUltiProjectile`, `Ash002Projectile1`
`Ash002Projectile2`, `Ash002Projectile3`, `Ash002UltiProjectile`, `Ash003Projectile1`, `Ash003Projectile2`, `Ash003Projectile3`, `Ash003UltiProjectile`, `Ash004Projectile1`
`Ash004Projectile2`, `Ash004Projectile3`, `Ash004UltiProjectile`, `Ash005Projectile1`, `Ash005Projectile2`, `Ash005Projectile3`, `Ash005UltiProjectile`, `Ash006Projectile1`
`Ash006Projectile2`, `Ash006Projectile3`, `Ash006UltiProjectile`, `Ash007Projectile1`, `Ash007Projectile2`, `Ash007Projectile3`, `Ash007UltiProjectile`, `Ash008Projectile1`
`Ash008Projectile2`, `Ash008Projectile3`, `Ash008UltiProjectile`, `AssaultShotgunGadgetProjectile`, `AssaultShotgunGadgetProjectile2`, `AssaultShotgunGadgetProjectileBuddy`, `AssaultShotgunGadgetProjectileCoinShower`, `AssaultShotgunGadgetProjectileCoinShowerBuddy`
`AssaultShotgunOverchargedProjectile`, `AssaultShotgunOverchargedProjectileSp1Buddy`, `AssaultShotgunOverchargedUltiProjectile`, `AssaultShotgunOverchargedUltiProjectile2`, `AssaultShotgunOverchargedUltiProjectile3`, `AssaultShotgunProjectile`, `AssaultShotgunProjectileSp1Buddy`, `AssaultShotgunUltiProjectile`
`AssaultShotgunUltiProjectile2`, `Attacher002Projectile`, `Attacher003Projectile`, `Attacher004Projectile`, `Attacher005Projectile`, `AttacherProjectile`, `AttacherProjectileOvercharged`, `AttractorCarrierProjectile`
`AttractorGadgetGroundedProjectile`, `AttractorGadgetPushbackProjectile`, `AttractorOrbiterProjectile`, `AttractorOrbiterProjectile2`, `AttractorOrbiterProjectile3`, `AttractorSuperProjectileMagnet`, `AxeJuggler002Projectile`, `AxeJuggler002Projectile2`
`AxeJuggler003Projectile`, `AxeJuggler003Projectile2`, `AxeJuggler004Projectile`, `AxeJuggler004Projectile2`, `AxeJuggler005Projectile`, `AxeJuggler005Projectile2`, `AxeJugglerOverchargedProjectile2`, `AxeJugglerProjectile`
`AxeJugglerProjectile2`, `BarkeepHealingProjectile`, `BarkeepOverchargedUltiProjectile`, `BarkeepProjectile`, `BarkeepUltiProjectile`, `Barley002Projectile`, `Barley002UltiProjectile`, `Barley003Projectile`
`Barley003UltiProjectile`, `Barley004Projectile`, `Barley004UltiProjectile`, `Barley005Projectile`, `Barley005UltiProjectile`, `Barley006Projectile`, `Barley006UltiProjectile`, `Barley007Projectile`
`Barley007UltiProjectile`, `Barley008Projectile`, `Barley008UltiProjectile`, `Barley009Projectile`, `Barley009UltiProjectile`, `BarrelBotOverchargedProjectile`, `BarrelBotProjectile`, `BarrelBotSpinProjectile`
`BaseballGadgetSkillStickyProjectile`, `BaseballGadgetSkillStickyProjectileBuddy`, `BaseballOverchargedUltiProjectile`, `BaseballOverchargedUltiProjectileChain`, `BaseballOverchargedUltiProjectileSticky`, `BaseballOverchargedUltiProjectileStickyChain`, `BaseballStickyProjectile`, `BaseballUltiProjectile`
`Bea002ChargedProjectile`, `Bea002Projectile`, `Bea002UltiProjectile`, `Bea003ChargedProjectile`, `Bea003Projectile`, `Bea003UltiProjectile`, `Bea004ChargedProjectile`, `Bea004Projectile`
`Bea004UltiProjectile`, `Bea005ChargedProjectile`, `Bea005Projectile`, `Bea005UltiProjectile`, `Bea006ChargedProjectile`, `Bea006Projectile`, `Bea006UltiProjectile`, `Bea007ChargedProjectile`
`Bea007Projectile`, `Bea007UltiProjectile`, `Bea008ChargedProjectile`, `Bea008Projectile`, `Bea008UltiProjectile`, `BeaOverchargedUltiProjectile`, `BeaOverchargedUltiProjectile2`, `BeameOverchargedUltiProjectile`
`Beamer002Projectile`, `Beamer002UltiProjectile`, `Beamer003Projectile`, `Beamer003UltiProjectile`, `Beamer004Projectile`, `Beamer004UltiProjectile`, `Beamer005Projectile`, `Beamer005UltiProjectile`
`Beamer006Projectile`, `Beamer006UltiProjectile`, `Beamer007Projectile`, `Beamer007UltiProjectile`, `Beamer008Projectile`, `Beamer008UltiProjectile`, `BeamerProjectile`, `BeamerUltiProjectile`
`BeeProjectile`, `BeeSniperChargedProjectile`, `BeeSniperCirclingProjectile`, `BeeSniperProjectile`, `BeeSniperUltiProjectile`, `Belle002Projectile`, `Belle002UltiProjectile`, `Belle003Projectile`
`Belle003UltiProjectile`, `Belle004Projectile`, `Belle004UltiProjectile`, `Belle005Projectile`, `Belle005UltiProjectile`, `Belle006Projectile`, `Belle006UltiProjectile`, `Belle007Projectile`
`Belle007UltiProjectile`, `Bibi002UltiProjectile`, `Bibi003UltiProjectile`, `Bibi005UltiProjectile`, `Bibi006UltiProjectile`, `Bibi007UltiProjectile`, `Bibi008UltiProjectile`, `Bibi009UltiProjectile`
`Bibi010UltiProjectile`, `Bibi011UltiProjectile`, `BlackHoleOverchargedUltiProjectile`, `BlackHolePet2Projectile`, `BlackHolePetProjectile`, `BlackHoleProjectile`, `BlackHoleUltiProjectile`, `BlowerProjectile`
`BlowerUltiOverchargedProjectile`, `BlowerUltiProjectile`, `Bo003Projectile`, `Bo003UltiProjectile`, `Bo004Projectile`, `Bo004UltiProjectile`, `Bo005Projectile`, `Bo005UltiProjectile`
`Bo006Projectile`, `Bo006UltiProjectile`, `Bo007Projectile`, `Bo007UltiProjectile`, `Bo008Projectile`, `Bo008UltiProjectile`, `Bo009Projectile`, `Bo009UltiProjectile`
`BoneThrowerProjectile`, `BoneThrowerUltiProjectile`, `Bonnie002ChainProjectile`, `Bonnie002Projectile`, `Bonnie002SmallProjectile`, `Bonnie003ChainProjectile`, `Bonnie003Projectile`, `Bonnie003SmallProjectile`
`Bonnie004ChainProjectile`, `Bonnie004Projectile`, `Bonnie004SmallProjectile`, `Bonnie005ChainProjectile`, `Bonnie005Projectile`, `Bonnie005SmallProjectile`, `Bonnie006ChainProjectile`, `Bonnie006Projectile`
`Bonnie006SmallProjectile`, `BoomBoxProjectile`, `BoomBoxProjectile_lvl2`, `BoomBoxProjectile_lvl3`, `BossProjectile`, `BossRaceBossLightningProjectile1`, `BossRaceBossLightningProjectile2`, `BossRaceBossLightningProjectile3`
`BossRaceBossProjectile`, `BossRaceBossRocketProjectile`, `Bow002Projectile`, `Bow002UltiProjectile`, `BowDudeGadgetSkillProjectile`, `BowDudeGadgetSkillProjectileBuddy`, `BowDudeOverchargedProjectile`, `BowDudeProjectile`
`BowDudeProjectileTripWire`, `BowDudeProjectileTripWireBuddy`, `BowDudeSpawnMineProjectile`, `BowDudeSpawnOverchargedMineProjectile`, `BrawlersMagnetProjectile1_lvl1`, `BrawlersMagnetProjectile1_lvl3`, `BrawlersMagnetProjectile2_lvl1`, `BrawlersMagnetProjectile2_lvl3`
`Brock002Projectile`, `Brock002ProjectileSecondary`, `Brock002UltiProjectile`, `Brock003Projectile`, `Brock003ProjectileSecondary`, `Brock003UltiProjectile`, `Brock004Projectile`, `Brock004ProjectileSecondary`
`Brock004UltiProjectile`, `Brock005Projectile`, `Brock005ProjectileSecondary`, `Brock005UltiProjectile`, `Brock006Projectile`, `Brock006ProjectileSecondary`, `Brock006UltiProjectile`, `Brock007Projectile`
`Brock007ProjectileSecondary`, `Brock007UltiProjectile`, `Brock008Projectile`, `Brock008ProjectileSecondary`, `Brock008UltiProjectile`, `Brock009Projectile`, `Brock009ProjectileSecondary`, `Brock009UltiProjectile`
`Brock010ProjectileBlack`, `Brock010ProjectileBlackSecondary`, `Brock010ProjectileBlue`, `Brock010ProjectileBlueSecondary`, `Brock010ProjectilePink`, `Brock010ProjectilePinkSecondary`, `Brock010ProjectileRed`, `Brock010ProjectileRedSecondary`
`Brock010ProjectileYellow`, `Brock010ProjectileYellowSecondary`, `Brock010UltiProjectileBlack`, `Brock010UltiProjectileBlue`, `Brock010UltiProjectilePink`, `Brock010UltiProjectileRed`, `Brock010UltiProjectileYellow`, `Brock011Projectile`
`Brock011ProjectileSecondary`, `Brock011UltiProjectile`, `Brock012OverchargedProjectile`, `Brock012OverchargedProjectileSecondary`, `Brock012Projectile`, `Brock012ProjectileSecondary`, `Brock012UltiOverchargedProjectile`, `Brock012UltiProjectile`
`Bronson002Projectile`, `Bronson002Projectile2`, `Bronson002UltiProjectile`, `Bronson002UltiProjectile2`, `Bronson003Projectile`, `Bronson003Projectile2`, `Bronson003UltiProjectile`, `Bronson003UltiProjectile2`
`Bronson0040Projectile2`, `Bronson004Projectile`, `Bronson004UltiProjectile`, `Bronson004UltiProjectile2`, `Bronson005Projectile`, `Bronson005Projectile2`, `Bronson005UltiProjectile`, `Bronson005UltiProjectile2`
`Bronson006Projectile`, `Bronson006Projectile2`, `Bronson006UltiProjectile`, `Bronson006UltiProjectile2`, `Bull002Projectile`, `Bull003Projectile`, `Bull004Projectile`, `Bull005Projectile`
`Bull006Projectile`, `Bull007Projectile`, `Bull008Projectile`, `Bull009Projectile`, `Bull011Projectile`, `Bull012Projectile`, `BullDudeGadgetSkillMarkEnemyProjectile`, `BullDudeGadgetSkillMarkEnemyProjectileBuddy`
`BullDudeOverchargedProjectile`, `BullDudeProjectile`, `Bulletstorm002LastShotProjectile`, `Bulletstorm002OnShellPickedUpProjectile`, `Bulletstorm002Projectile`, `Bulletstorm002ShellProjectile`, `Bulletstorm002UltiMarkedProjectile`, `Bulletstorm002UltiProjectile`
`BulletstormLastShotProjectile`, `BulletstormOnShellPickedUpProjectile`, `BulletstormProjectile`, `BulletstormShellProjectile`, `BulletstormUltiMarkedProjectile`, `BulletstormUltiOverchargedMarkedProjectile`, `BulletstormUltiOverchargedProjectile`, `BulletstormUltiProjectile`
`Buster002Projectile`, `Buster002UltiProjectile`, `Buster003Projectile`, `Buster003UltiProjectile`, `Buster004Projectile`, `Buster004UltiProjectile`, `Buster005Projectile`, `Buster005UltiProjectile`
`Buzz002Projectile`, `Buzz002UltiProjectile`, `Buzz003Projectile`, `Buzz003UltiProjectile`, `Buzz005Projectile`, `Buzz005UltiProjectile`, `Buzz006Projectile`, `Buzz006UltiProjectile`
`Buzz007OverchargedProjectile`, `Buzz007OverchargedUltiProjectile`, `Buzz007Projectile`, `Buzz007UltiProjectile`, `Buzz008Projectile`, `Buzz008UltiProjectile`, `Buzz009Projectile`, `Buzz009UltiProjectile`
`Buzz010Projectile`, `Buzz010UltiProjectile`, `Byron002Projectile`, `Byron002UltiProjectile`, `Byron003Projectile`, `Byron004Projectile`, `Byron004UltiProjectile`, `Byron005Projectile`
`Byron005UltiProjectile`, `Byron006Projectile`, `Byron006UltiProjectile`, `Byroon003UltiProjectile`, `CactusBonusSkillCoverProjectile`, `CactusBonusSkillCoverProjectileBuddy`, `CactusOverchargedUltiProjectile`, `CactusProjectile`
`CactusSpike`, `CactusSpikeGadget`, `CactusSpikeGadgetBuddy`, `CactusUltiProjectile`, `CannonGirlChainProjectile`, `CannonGirlExplosionProjectileOvercharged`, `CannonGirlProjectile`, `CannonGirlSmallProjectile`
`Carl002Projectile`, `Carl002Projectile2`, `Carl003Projectile`, `Carl003Projectile2`, `Carl004Projectile`, `Carl004Projectile2`, `Carl005Projectile`, `Carl005Projectile2`
`Carl006Projectile`, `Carl006Projectile2`, `Carl007Projectile`, `Carl007Projectile2`, `Carl008Projectile`, `Carl008Projectile2`, `Carl009Projectile`, `Carl009Projectile2`
`Carl010Projectile`, `Carl010Projectile2`, `Carl011Projectile`, `Carl011Projectile2`, `Chester002Projectile`, `Chester002ProjectileSP`, `Chester002UltiProjectileExploding`, `Chester002UltiProjectilePoisoning`
`Chester002UltiProjectileStunning`, `Chester003Projectile`, `Chester003ProjectileSP`, `Chester003UltiProjectileExploding`, `Chester003UltiProjectilePoisoning`, `Chester003UltiProjectileStunning`, `Chester004Projectile`, `Chester004ProjectileSP`
`Chester004UltiProjectileExploding`, `Chester004UltiProjectilePoisoning`, `Chester004UltiProjectileStunning`, `Chester005Projectile`, `Chester005ProjectileSP`, `Chester005UltiProjectileExploding`, `Chester005UltiProjectilePoisoning`, `Chester005UltiProjectileStunning`
`Chester006Projectile`, `Chester006ProjectileSP`, `Chester006UltiProjectileExploding`, `Chester006UltiProjectilePoisoning`, `Chester006UltiProjectileStunning`, `ChesterOverchargedUltiProjectile`, `ChesterOverchargedUltiProjectilePoisoning`, `Chronomancer002Projectile`
`Chronomancer002ProjectileSecondary`, `Chronomancer002ProjectileStasis`, `Chronomancer002UltiProjectile`, `Chronomancer003Projectile`, `Chronomancer003ProjectileSecondary`, `Chronomancer003UltiProjectile`, `ChronomancerProjectile`, `ChronomancerProjectileSecondary`
`ChronomancerProjectileStasis`, `ChronomancerProjectileStasisSecondary`, `ChronomancerUltiHyperProjectile`, `ChronomancerUltiProjectile`, `ClusterBombOverchargedSummonProjectile`, `ClusterBombProjectile`, `ClusterBombProjectile2`, `ClusterBombSummonProjectile`
`Cocooner002Projectile`, `Cocooner002Projectile2`, `Cocooner002UltiProjectile`, `Cocooner003Projectile`, `Cocooner003Projectile2`, `Cocooner003UltiProjectile`, `Cocooner004Projectile`, `Cocooner004Projectile2`
`Cocooner004UltiProjectile`, `CocoonerOverchargedUltiProjectile`, `CocoonerProjectile`, `CocoonerProjectile2`, `CocoonerUltiProjectile`, `Colette002Projectile`, `Colette003Projectile`, `Colette004Projectile`
`Colette005Projectile`, `Colette006Projectile`, `Colette007Projectile`, `Colette008Projectile`, `Colette009Projectile`, `Colt002Projectile`, `Colt002UltiProjectile`, `Colt003Projectile`
`Colt003UltiProjectile`, `Colt004Projectile`, `Colt004UltiProjectile`, `Colt005Projectile`, `Colt005UltiProjectile`, `Colt006Projectile`, `Colt006UltiProjectile`, `Colt007Projectile`
`Colt007UltiProjectile`, `Colt008Projectile`, `Colt008UltiProjectile`, `Colt009Projectile`, `Colt009UltiProjectile`, `Colt010Projectile`, `Colt010UltiProjectile`, `Colt011Projectile`
`Colt011UltiProjectile`, `ColtRankedOverchargedBuddyProjectile`, `ColtRankedOverchargedProjectile`, `ColtRankedOverchargedUltiProjectile`, `Conductor002Projectile`, `Conductor002UltiProjectile`, `Conductor003Projectile`, `Conductor003UltiProjectile`
`Conductor004Projectile`, `Conductor004UltiProjectile`, `ConductorOverchargedProjectile`, `ConductorProjectile`, `ConductorUltiProjectile`, `ControllerArchetypeCollabProjectileLvl1`, `ControllerArchetypeCollabProjectileLvl2`, `ControllerArchetypeCollabProjectileLvl3`
`ControllerProjectile`, `ControllerUltiOverchargedProjectile`, `ControllerUltiProjectile`, `CookerProjectile`, `CoopRangedEnemyProjectile`, `Cordelius002Projectile`, `Cordelius002UltiProjectile`, `Cordelius003Projectile`
`Cordelius003UltiProjectile`, `Cordelius004Projectile`, `Cordelius004UltiProjectile`, `Cordelius005Projectile`, `Cordelius005UltiProjectile`, `Cordelius006Projectile`, `Cordelius006UltiProjectile`, `Crab002Projectile`
`Crab002UltiProjectile`, `CrabOverchargedUltiProjectile`, `CrabOverchargedUltiReturnProjectile`, `CrabProjectile`, `CrabUltiProjectile`, `CrossBomberProjectile`, `CrossBomberProjectile2`, `CrossBomberUltiProjectile`
`CrossBomberUltiProjectile2`, `Crow002Projectile`, `Crow002UltiProjectile`, `Crow003Projectile`, `Crow003UltiProjectile`, `Crow004Projectile`, `Crow004UltiProjectile`, `Crow005Projectile`
`Crow005UltiProjectile`, `Crow006Projectile`, `Crow006UltiProjectile`, `Crow007Projectile`, `Crow007UltiProjectile`, `Crow009Projectile`, `Crow009UltiProjectile`, `Crow010OverchargedProjectile`
`Crow010OverchargedProjectile2`, `Crow010OverchargedUltiProjectile`, `Crow010OverchargedUltiProjectile2`, `Crow010Projectile`, `Crow010UltiProjectile`, `CrowOverchargedProjectile`, `CrowOverchargedProjectile2`, `CrowOverchargedUltiProjectile`
`CrowOverchargedUltiProjectile2`, `CrowProjectile`, `CrowProjectileFlame`, `CrowThrowPoisonDaggerSkillProjectile`, `CrowThrowPoisonDaggerSkillProjectileBuddy`, `CrowThrowPoisonDaggerSkillProjectileBuddyChain`, `CrowUltiProjectile`, `CrowUltiProjectileFlame`
`DamageDealerArchetypeCollabProjectileLvl1`, `DamageDealerArchetypeCollabProjectileLvl3`, `DamageDealerArchetypeCollabProjectileLvl3Return`, `Dancer002ProjectileDouble`, `Dancer002ProjectileSingle`, `Dancer002ProjectileTriple`, `Dancer002ProjectileUlti`, `Dancer003ProjectileDouble`
`Dancer003ProjectileSingle`, `Dancer003ProjectileTriple`, `Dancer003ProjectileUlti`, `DancerOverchargedProjectileUlti`, `DancerProjectileDouble`, `DancerProjectileSingle`, `DancerProjectileTriple`, `DancerProjectileUlti`
`Darryl002Projectile`, `Darryl003Projectile`, `Darryl004Projectile`, `Darryl005Projectile`, `Darryl006Projectile`, `Darryl007Projectile`, `Darryl008Projectile`, `Darryl009Projectile`
`Darryl010Projectile`, `DeadMariachiOverchargedProjectile`, `DeadMariachiOverchargedUltiProjectile`, `DeadMariachiProjectile`, `DeadMariachiUltiProjectile`, `DeadMariachi_CleanseProjectile`, `DeadMariachi_CleanseProjectileBuddy`, `DemonicPowerProjectile`
`DemonicProjectile`, `DemonicProjectileBoomerang`, `DemonicSoulCollectorProjectile`, `Digger002DrillProjectile`, `Digger002Projectile`, `Digger002ProjectileBounce`, `Digger002ProjectileBounceSP`, `Digger002ProjectileShrapnel`
`Digger003Projectile`, `Digger003ProjectileBounce`, `Digger003ProjectileBounceSP`, `Digger003ProjectileShrapnel`, `DiggerDrillOverchargedProjectile`, `DiggerDrillProjectile`, `DiggerProjectile`, `DiggerProjectileBounce`
`DiggerProjectileBounceSP`, `DiggerProjectileShrapnel`, `DoorMan002Projectile`, `DoorMan003Projectile`, `DoorMan004Projectile`, `DoorMan005Projectile`, `DoorManCaneGadgetProjectile`, `DoorManCaneGadgetProjectile2`
`DoorManProjectile`, `DragonRider002Projectile`, `DragonRider003Projectile`, `DragonRiderDragon002Projectile`, `DragonRiderDragon003Projectile`, `DragonRiderDragonOverchargedProjectile`, `DragonRiderDragonProjectile`, `DragonRiderProjectile`
`DuelistOverchargedUltiProjectile`, `DuelistProjectile`, `DuelistSilenceProjectile`, `DuelistUltiProjectile`, `DummyProjectileForBasketBrawl`, `DummyProjectileForCTF`, `DummyProjectileForLaserBall`, `DummyProjectileForLaserBallBurning`
`DummyProjectileForLoveBomb`, `DuplicatorProjectile`, `DuplicatorUltiProjectile`, `ElectroSniperBounceProjectile`, `ElectroSniperMutantProjectile`, `ElectroSniperOverchargedUltiProjectile`, `ElectroSniperProjectile`, `ElectroSniperSecondaryProjectile_001`
`ElectroSniperSecondaryProjectile_002`, `ElectroSniperSecondaryProjectile_003`, `ElectroSniperSecondaryProjectile_004`, `ElectroSniperSecondaryProjectile_005`, `ElectroSniperSecondaryProjectile_006`, `ElectroSniperSecondaryProjectile_007`, `ElectroSniperUltiProjectile`, `Emz002Projectile`
`Emz003Projectile`, `Emz004Projectile`, `Emz005Projectile`, `Emz006Projectile`, `Emz007Projectile`, `EndOfLineProjectile`, `EndOfLineProjectile_lvl3`, `Enrager002Projectile`
`Enrager003Projectile`, `Enrager004Projectile`, `Enrager005Projectile`, `Enrager006Projectile`, `Enrager007Projectile`, `Enrager008OverchargedLongRangeProjectile`, `Enrager008OverchargedProjectile`, `Enrager008Projectile`
`Enrager009Projectile`, `Enrager010Projectile`, `EnragerOverchargedLongRangeProjectile`, `EnragerProjectile`, `EnragerPullProjectile`, `EnragerPullProjectileBuddy`, `Eve006Projectile1`, `Eve006Projectile2`
`Eve006Projectile3`, `Eve006SpawnProjectile`, `Eve006UltiProjectile`, `Fang003Projectile`, `Fang003Projectile2`, `Fang004Projectile`, `Fang004Projectile2`, `Fang005Projectile`
`Fang005Projectile2`, `Fang006Projectile`, `Fang006Projectile2`, `Fang007Projectile`, `Fang007Projectile2`, `Fang008Projectile`, `Fang008Projectile2`, `Fang009Projectile`
`Fang009Projectile2`, `FireDude002Projectile`, `FireDude002UltiProjectile`, `FireDude003Projectile`, `FireDude003UltiProjectile`, `FireDude004Projectile`, `FireDude004UltiProjectile`, `FireDude005Projectile`
`FireDude005UltiProjectile`, `FireDude006Projectile`, `FireDude006UltiProjectile`, `FireDudeBonusSkillSpillProjectile`, `FireDudeCirclingProjectile`, `FireDudeOverchargedProjectile`, `FireDudeOverchargedUltiProjectile`, `FireDudeProjectile`
`FireDudeUltiProjectile`, `FishTankUltiProjectile`, `FishTankUltiProjectileSmall`, `Flea002Projectile1`, `Flea002Projectile2`, `Flea002Projectile3`, `Flea002SpawnProjectile`, `Flea002UltiProjectile`
`Flea003Projectile1`, `Flea003Projectile2`, `Flea003Projectile3`, `Flea003SpawnProjectile`, `Flea003UltiProjectile`, `Flea004Projectile1`, `Flea004Projectile2`, `Flea004Projectile3`
`Flea004SpawnProjectile`, `Flea004UltiProjectile`, `Flea005Projectile1`, `Flea005Projectile2`, `Flea005Projectile3`, `Flea005SpawnProjectile`, `Flea005UltiProjectile`, `FleaOverchargedSpawnProjectile`
`FleaProjectile1`, `FleaProjectile2`, `FleaProjectile3`, `FleaProjectileNano4`, `FleaSpawnProjectile`, `FleaUltiProjectile`, `Frank002Projectile`, `Frank002UltiProjectile`
`Frank004Projectile`, `Frank004UltiProjectile`, `Frank005Projectile`, `Frank005UltiProjectile`, `Frank006Projectile`, `Frank006UltiProjectile`, `Frank007Projectile`, `Frank007UltiProjectile`
`Frank008Projectile`, `Frank008UltiProjectile`, `Frank009Projectile`, `Frank009UltiProjectile`, `Fury002Projectile`, `Fury002ProjectileCrit`, `Fury002UltiProjectile`, `FuryOverchargedUltiProjectile`
`FuryOverchargedUltiProjectileReturn`, `FuryProjectile`, `FuryProjectileCrit`, `FuryUltiProjectile`, `FutureGirlGadgetProjectile`, `FutureGirlOverchargedUltiProjectile`, `FutureGirlProjectile`, `FutureGirlTurretTetherOverchargedProjectile`
`FutureGirlTurretTetherProjectile`, `FutureGirlUltiProjectile`, `Gale002Projectile`, `Gale002UltiProjectile`, `Gale003Projectile`, `Gale003UltiProjectile`, `Gale004Projectile`, `Gale004UltiProjectile`
`Gale005Projectile`, `Gale005UltiProjectile`, `Gale006Projectile`, `Gale006UltiProjectile`, `Geisha002TransformedProjectile`, `Geisha002UltiProjectile`, `GeishaTransformedProjectile`, `GeishaUltiProjectile`
`GeishaUltiProjectileOvercharged`, `Gene002Projectile`, `Gene002Projectile2`, `Gene002UltiProjectile`, `Gene002UltiProjectile2`, `Gene003Projectile`, `Gene003Projectile2`, `Gene003UltiProjectile`
`Gene003UltiProjectile2`, `Gene004Projectile`, `Gene004Projectile2`, `Gene004UltiProjectile`, `Gene004UltiProjectile2`, `Gene005Projectile`, `Gene005Projectile2`, `Gene005UltiProjectile`
`Gene005UltiProjectile2`, `Gene006Projectile`, `Gene006Projectile2`, `Gene006UltiProjectile`, `Gene006UltiProjectile2`, `Gene007Projectile`, `Gene007Projectile2`, `Gene007UltiProjectile`
`Gene007UltiProjectile2`, `GeneHomingNanoProjectile`, `GeneHomingProjectile`, `Gladiator002Projectile`, `Gladiator002ProjectileFire`, `Gladiator002UltiProjectile`, `GladiatorGadgetSkillProjectileAmp`, `GladiatorGadgetSkillProjectileWall`
`GladiatorOverchargedUltiProjectile`, `GladiatorProjectile`, `GladiatorProjectileFire`, `GladiatorUltiProjectile`, `Godzilla1UltiProjectile`, `Godzilla2UltiProjectile`, `GodzillaClawsProjectile`, `GodzillaUltiProjectile`
`Griff002Projectile`, `Griff002ProjectileSp1Buddy`, `Griff002UltiProjectile`, `Griff002UltiProjectile2`, `Griff003Projectile`, `Griff003ProjectileSp1Buddy`, `Griff003UltiProjectile`, `Griff003UltiProjectile2`
`Griff004Projectile`, `Griff004ProjectileSp1Buddy`, `Griff004UltiProjectile`, `Griff004UltiProjectile2`, `Griff005Projectile`, `Griff005ProjectileSp1Buddy`, `Griff005UltiProjectile`, `Griff005UltiProjectile2`
`Griff006Projectile`, `Griff006ProjectileSp1Buddy`, `Griff006UltiProjectile`, `Griff006UltiProjectile2`, `Griff007Projectile`, `Griff007ProjectileSp1Buddy`, `Griff007UltiProjectile`, `Griff007UltiProjectile2`
`Grom002Projectile`, `Grom002Projectile2`, `Grom002UltiProjectile`, `Grom002UltiProjectile2`, `Grom003Projectile`, `Grom003Projectile2`, `Grom003UltiProjectile`, `Grom003UltiProjectile2`
`Grom004Projectile`, `Grom004Projectile2`, `Grom004UltiProjectile`, `Grom004UltiProjectile2`, `Grom005Projectile`, `Grom005Projectile2`, `Grom005UltiProjectile`, `Grom005UltiProjectile2`
`Grom006Projectile`, `Grom006Projectile2`, `Grom006UltiProjectile`, `Grom006UltiProjectile2`, `GunslingerBigProjectile`, `GunslingerDoubleShotProjectile`, `GunslingerDoubleShotProjectileBuddy`, `GunslingerOverchargedProjectile`
`GunslingerOverchargedUltiProjectile`, `GunslingerProjectile`, `GunslingerSilverBulletProjectile`, `GunslingerSilverBulletProjectileBuddy`, `GunslingerUltiProjectile`, `Gus002Projectile`, `Gus002UltiProjectile`, `Gus003Projectile`
`Gus003UltiProjectile`, `Gus004Projectile`, `Gus004UltiProjectile`, `Gus005Projectile`, `Gus005UltiProjectile`, `Gus006Projectile`, `Gus006UltiProjectile`, `Gus007Projectile`
`Gus007UltiProjectile`, `GusOverchargedAreaEffectProjectile`, `GusOverchargedUltiProjectile`, `HammerDudeGadgetSkillAttractionBuddyProjectile`, `HammerDudeGadgetSkillAttractionProjectile`, `HammerDudeGadgetSkillNoiseCancelBuddyProjectile`, `HammerDudeGadgetSkillNoiseCancelProjectile`, `HammerDudeOverchargedUltiProjectile`
`HammerDudeProjectile`, `HammerDudeStarPowerProjectile`, `HammerDudeUltiProjectile`, `HammerDudeWeaponOverchargedProjectile`, `HoldBallResetTrail`, `HookProjectile`, `HookProjectile2`, `HookTimeProjectile_lvl1`
`HookTimeProjectile_lvl3`, `HookUltiOverchargedProjectile`, `HookUltiOverchargedProjectile2`, `HookUltiProjectile`, `HookUltiProjectile2`, `IceDudeOverchargedUltiProjectile`, `IceDudeProjectile`, `IceDudeUltiProjectile`
`Jessie002Projectile1`, `Jessie002Projectile2`, `Jessie002Projectile3`, `Jessie002UltiProjectile`, `Jessie003Projectile1`, `Jessie003Projectile2`, `Jessie003Projectile3`, `Jessie003UltiProjectile`
`Jessie004Projectile1`, `Jessie004Projectile2`, `Jessie004Projectile3`, `Jessie004UltiProjectile`, `Jessie005Projectile1`, `Jessie005Projectile2`, `Jessie005Projectile3`, `Jessie005UltiProjectile`
`Jessie006Projectile1`, `Jessie006Projectile2`, `Jessie006Projectile3`, `Jessie006UltiProjectile`, `Jessie007Projectile1`, `Jessie007Projectile2`, `Jessie007Projectile3`, `Jessie007UltiProjectile`
`Jessie008Projectile1`, `Jessie008Projectile2`, `Jessie008Projectile3`, `Jessie008UltiProjectile`, `Jessie009Projectile1`, `Jessie009Projectile2`, `Jessie009Projectile3`, `Jessie009UltiProjectile`
`Jessie010Projectile1`, `Jessie010Projectile2`, `Jessie010Projectile3`, `Jessie010UltiProjectile`, `Jessie011Projectile1`, `Jessie011Projectile2`, `Jessie011Projectile3`, `Jessie011UltiProjectile`
`JessieTurret002Projectile`, `JessieTurret003Projectile`, `JessieTurret004Projectile`, `JessieTurret005Projectile`, `JessieTurret006Projectile`, `JessieTurret007Projectile`, `JessieTurret008Projectile`, `JessieTurret009Projectile`
`JessieTurret010Projectile`, `JessieTurret011Projectile`, `JesterProjectile`, `JesterProjectileSP`, `JesterUltiProjectileExploding`, `JesterUltiProjectilePoisoning`, `JesterUltiProjectileStunning`, `JetpackGirl002Projectile`
`JetpackGirl002UltiProjectile`, `JetpackGirl003Projectile`, `JetpackGirl003UltiProjectile`, `JetpackGirl004Projectile`, `JetpackGirl004UltiProjectile`, `JetpackGirl005Projectile`, `JetpackGirl005UltiProjectile`, `JetpackGirl006Projectile`
`JetpackGirl006UltiProjectile`, `JetpackGirl007Projectile`, `JetpackGirl007UltiProjectile`, `JetpackGirl008Projectile`, `JetpackGirl008UltiProjectile`, `JetpackGirl009Projectile`, `JetpackGirl009UltiProjectile`, `JetpackGirlOverchargedUltiProjectile`
`JetpackGirlProjectile`, `JetpackGirlUltiProjectile`, `JetpackProjectileDamage`, `JetpackProjectileDamageAndSlow`, `KatanaKidFullChargeProjectile`, `KatanaKidGadgetSkillFishNetProjectile`, `KatanaKidProjectile`, `KickerDude002Projectile`
`KickerDude002Projectile2`, `KickerDudeMinesProjectile`, `KickerDudeProjectile`, `KickerDudeProjectile2`, `KnightOverchargedUltiProjectile`, `KnightProjectile1`, `KnightProjectile2`, `KnightProjectile3`
`KnightUltiProjectile`, `LeaperShotgunProjectile`, `Leon002Projectile`, `Leon003Projectile`, `Leon004Projectile`, `Leon005Projectile`, `Leon006Projectile`, `Leon007Projectile`
`Leon008Projectile`, `Leon009Projectile`, `Leon010OverchargedProjectile`, `Leon010Projectile`, `LeonDefOverchargedProjectile`, `LeonDefProjectile`, `LeonDefProjectileMutation`, `LightyearFlightProjectile`
`LightyearFlightUltiProjectile`, `LightyearLaserProjectile`, `LightyearLaserUltiProjectile`, `Lolla002Projectile`, `Lolla002UltiProjectile`, `Lolla003Projectile`, `Lolla003UltiProjectile`, `Lolla004Projectile`
`Lolla004UltiProjectile`, `Lolla005Projectile`, `Lolla005UltiProjectile`, `Lolla006Projectile`, `Lolla006UltiProjectile`, `Lolla007Projectile`, `Lolla007UltiProjectile`, `Lolla008Projectile`
`Lolla008UltiProjectile`, `Lou002Projectile`, `Lou002UltiProjectile`, `Lou003Projectile`, `Lou003UltiProjectile`, `Lou004Projectile`, `Lou004UltiProjectile`, `Lou005Projectile`
`Lou005UltiProjectile`, `Lou006Projectile`, `Lou006UltiProjectile`, `Lou007Projectile`, `Lou007UltiProjectile`, `MagicalGirlBonusSkillFlyAreaProjectile`, `MagicalGirlBonusSkillProjectileHealing`, `MagicalGirlProjectile`
`MagicalGirlProjectile2`, `MagicalGirlProjectile2HealingSP`, `MagicalGirlProjectileHealingSP`, `Maisie002Projectile`, `Maisie003Projectile`, `Maisie004Projectile`, `Maisie005Projectile`, `MaisieOverchargedProjectile`
`MaisieProjectile`, `Max002Projectile`, `Max003Projectile`, `Max004Projectile`, `Max005Projectile`, `Max006Projectile`, `Max007Projectile`, `Mecha002Projectile`
`Mecha002UltiProjectile`, `Mecha003Projectile`, `Mecha003UltiProjectile`, `Mecha004Projectile`, `Mecha004UltiProjectile`, `Mecha005Projectile`, `Mecha005UltiProjectile`, `Mecha006Projectile`
`Mecha006UltiProjectile`, `Mecha007BuddyOverchargedProjectile`, `Mecha007OverchargedProjectile`, `Mecha007OverchargedUltiProjectile`, `Mecha007Projectile`, `Mecha007UltiProjectile`, `MechaDude007BigProjectileHyperChargedBuddy`, `MechaDude007ProjectileHyperCharged`
`MechaDudeAngelSendItProjectile`, `MechaDudeAngelSendItProjectileBuddy`, `MechaDudeBigProjectile`, `MechaDudeBigProjectileHyperChargedBuddy`, `MechaDudeCybernoodlesSendItProjectile`, `MechaDudeCybernoodlesSendItProjectileBuddy`, `MechaDudeCybernoodlesSendItProjectileBuddyChroma1`, `MechaDudeCybernoodlesSendItProjectileBuddyChroma2`
`MechaDudeCybernoodlesSendItProjectileChroma1`, `MechaDudeCybernoodlesSendItProjectileChroma2`, `MechaDudeGoldSendItProjectile`, `MechaDudeGoldSendItProjectileBuddy`, `MechaDudeJaguarSendItProjectile`, `MechaDudeJaguarSendItProjectileBuddy`, `MechaDudeMonsterTruckSendItProjectile`, `MechaDudeMonsterTruckSendItProjectileBuddy`
`MechaDudePirateSendItProjectile`, `MechaDudePirateSendItProjectileBuddy`, `MechaDudeProjectile`, `MechaDudeProjectileHyperCharged`, `MechaDudeRareSendItProjectile`, `MechaDudeRareSendItProjectileBuddy`, `MechaDudeRhinoSendItProjectile`, `MechaDudeRhinoSendItProjectileBuddy`
`MechaDudeSendItProjectile`, `MechaDudeSendItProjectileBuddy`, `MechaDudeSilverSendItProjectile`, `MechaDudeSilverSendItProjectileBuddy`, `MechaVanMeleeNinjaStabProjectile`, `MechaVanSniperLongRangeProjectile`, `MechaVanSniperPiercingProjectile`, `MechanicOverchargedTurretElecProj`
`MechanicOverchargedTurretElecProj2`, `MechanicOverchargedTurretElecProj3`, `MechanicOverchargedTurretProjectile`, `MechanicOverchargedUltiProjectile`, `MechanicProjectile1`, `MechanicProjectile2`, `MechanicProjectile3`, `MechanicTurretProjectile`
`MechanicUltiProjectile`, `Meeple002Projectile`, `Meeple002UltiProjectile`, `Meeple002WallProjectile`, `Meeple003Projectile`, `Meeple003UltiProjectile`, `Meeple003WallProjectile`, `MeepleOverchargedUltiProjectile`
`MeepleProjectile`, `MeepleUltiProjectile`, `MeepleWallProjectile`, `MegaBossAssaultShotgunBombExplosion`, `MegaBossAssaultShotgunGadgetProjectile`, `MegaBossAssaultShotgunOverchargedUltiProjectile`, `MegaBossAssaultShotgunOverchargedUltiProjectile2`, `MegaBossAssaultShotgunOverchargedUltiProjectile3`
`MegaBossAssaultShotgunProjectile`, `MegaBossAssaultShotgunProjectileBig`, `MegaBossAssaultShotgunProjectileCoin`, `MegaBossAssaultShotgunProjectileExtraBig`, `MegaBossAssaultShotgunUltiProjectile`, `MegaBossAssaultShotgunUltiProjectile2`, `MegaBossBlackHoleBoomerangWellChainProjectile`, `MegaBossBlackHoleBoomerangWellProjectile`
`MegaBossBlackHoleExplosionPetProjectile`, `MegaBossBlackHoleGravityWellProjectile`, `MegaBossBlackHoleProjectile`, `MegaBossBlackHoleShieldPetProjectile`, `MegaBossBlackHoleUltiExplodingPetProjectile`, `MegaBossBlackHoleUltiShieldPetProjectile`, `MegaBossBlackholeSpreadProjectile`, `MegaBossBlackholeSpreadProjectileReturn`
`MegaBossCactusFrag`, `MegaBossCactusPetShoot`, `MegaBossCactusProjectile`, `MegaBossCactusProjectileSecond`, `MegaBossCactusPushAwayFrag`, `MegaBossCactusUltiProjectile`, `MegaBossCrossBomberProjectile`, `MegaBossCrossBomberProjectile2`
`MegaBossCrossBomberSecondProjectile`, `MegaBossCrossBomberSummonPet`, `MegaBossCrossBomberUltiProjectile`, `MegaBossCrossBomberUltiProjectile2`, `MegaBossCrowJumpProjectile`, `MegaBossCrowJumpProjectileChain`, `MegaBossCrowProjectile`, `MegaBossCrowSwampProjectile`
`MegaBossCrowSwampProjectileLarge`, `MegaBossDgProjectile`, `MegaBossDgSpawn`, `MegaBossDgSpawnProjectile`, `MegaBossDragonCirclingProjectile`, `MegaBossDragonCrowBoomrangProjectile`, `MegaBossDragonCrowBoomrangProjectile2`, `MegaBossDragonCrowBoomrangProjectile2L3`
`MegaBossDragonCrowBoomrangProjectileL3`, `MegaBossDragonCrowProjectile`, `MegaBossDragonCrowSummon`, `MegaBossDragonCrowUltiProjectile`, `MegaBossDragonFireAreaExplosionProjectile`, `MegaBossDragonFireProjectile`, `MegaBossDragonFireProjectileBig`, `MegaBossDuoAlphabetProjectile`
`MegaBossDuoAlphabetProjectileBig`, `MegaBossFinxCreateKit`, `MegaBossFinxProjectile`, `MegaBossFinxProjectileSecondary`, `MegaBossFinxReturnChronomancerProjectile`, `MegaBossFinxReturnChronomancerProjectileSecondary`, `MegaBossFinxSpawnKittensProjectile`, `MegaBossFinxTimeRiftProjectile`
`MegaBossFinxTimeStopProjectile`, `MegaBossFinxTimebendProjectile`, `MegaBossFrankCreateDemon`, `MegaBossFrankGroundSpikeProjectile`, `MegaBossFrankProjectile`, `MegaBossFrankSpawnAdd`, `MegaBossFrankUltiProjectile`, `MegaBossGhostProjectile`
`MegaBossKatanaKidLobbedFishProjectile`, `MegaBossMaisieBigProjectile`, `MegaBossMaisieCreateExplosion`, `MegaBossMaisieExplosionProjectile`, `MegaBossMaisieProjectile`, `MegaBossMaisieSummonTurret`, `MegaBossMaisieTurretProjectile`, `MegaBossMosquitoProjectile`
`MegaBossMosquitoProjectileLarge`, `MegaBossOverchargedCrossBomberUltiProjectile`, `MegaBossOverchargedCrossBomberUltiProjectile2`, `MegaBossPercenterProjectile`, `MegaBossPercenterProjectileLarge`, `MegaBossPercenterProjectileSmall`, `MegaBossPercenterSpawnTurrentProjectile`, `MegaBossPercenterThrowProjectile`
`MegaBossPercenterTurrentPetProjectile`, `MegaBossRocketGirlClusterProjectile`, `MegaBossRocketGirlMatryoshkaProjectile`, `MegaBossRocketGirlProjectileBasic`, `MegaBossRocketGirlRainProjectile`, `MegaBossRocketGirlStreamProjectile`, `MegaBossRocketGirlUltiProjectile`, `MegaBossShamanBearUltiProjectile`
`MegaBossShamanProjectile`, `MegaBossShamanUltiProjectile`, `MegaBossSpikeSummonPet`, `MegaBossSplitterProjectile`, `MegaBossSplitterProjectilePierce`, `MegaBossSplitterProjectileSlow`, `MegaBossSplitterSpawnRobotsShoot`, `MegaBossSplitterSpawnRobotsThrow`
`MegaBossStickyBombOverchargedUltiProjectile`, `MegaBossStickyBombOverchargedUltiProjectileBounce1`, `MegaBossStickyBombOverchargedUltiProjectileBounce2`, `MegaBossStickyBombOverchargedUltiProjectileBounce3`, `MegaBossStickyBombOverchargedUltiProjectileBounce4`, `MegaBossStickyBombProjectile`, `MegaBossStickyBombProjectileLarge`, `MegaBossStickyBombUltiBulletExplodeProjectile`
`MegaBossStickyBombUltiBulletExplodeProjectileLarge`, `MegaBossStickyBombUltiProjectile`, `MegaBossTrickshotDude2Projectile`, `MegaBossTrickshotDude2ProjectileLarge`, `MegaBossTrickshotDude2ProjectileLargeExtra`, `MegaBossTrickshotDude2UltiProjectile`, `MegaBossTrickshotDudeProjectile`, `MegaBossTrickshotDudeProjectileLarge`
`MegaBossTrickshotDudeProjectileLargeExtra`, `MegaBossTrickshotDudeUltiProjectile`, `MegaBossTwinsShotgunProjectile`, `MegaBossTwinsThrowerProjectile`, `MegaBossVecAttackSlowProjectile`, `MegaBossVecProjectileBlackholeDistance`, `MegaBossVecProjectileDropClock`, `MegaBossVecProjectileFreeze`
`MegaBossVecProjectileLong`, `MegaBossVecProjectileRockExplosion`, `MegaBossVecProjectileRockExplosionProjectiles`, `MegaBossVecTeleport`, `MegaKatanaKidFishProjectile`, `MegaKatanaKidHookProjectile`, `MegaKatanaKidHookProjectile2`, `MegaKatanaKidProjectile`
`MegaKenjiProjectileDeath`, `MegaKenjiProjectileFast360`, `MegaKenjiProjectileSlowBounce`, `MegaKenjiProjectileSpawnKenji`, `MegaKenjiProjectileSpawnRobot`, `MegaSamuraiRangedEnemyProjectile`, `MegaTickProjectile`, `MegaTickSecondProjectile`
`MegaTickSummonProjectile`, `MegaTickSummonProjectileLarge`, `MegaTickSummonProjectileMid`, `Mender002Projectile`, `Mender002UltiProjectile`, `MenderProjectile`, `MenderUltiOverchargedProjectile`, `MenderUltiProjectile`
`Mike004Projectile`, `Mike004UltiProjectile`, `Mike005Projectile`, `Mike005UltiProjectile`, `Mike006Projectile`, `Mike006UltiProjectile`, `Mike007Projectile`, `Mike007UltiProjectile`
`Mike008Projectile`, `Mike008UltiProjectile`, `Mike009Projectile`, `Mike009UltiProjectile`, `Mike010Projectile`, `Mike010UltiProjectile`, `Mike011Projectile`, `Mike011UltiProjectile`
`Mike012OverchargedClusterProjectile`, `Mike012OverchargedProjectile`, `Mike012OverchargedUltiProjectile`, `Mike012Projectile`, `Mike012UltiProjectile`, `MinigunDudeOverchargedUltiProjectile`, `MinigunDudeProjectile`, `MinigunDudeProjectileNano`
`MinigunDudeUltiProjectile`, `MobaBigKaijuProjectile`, `MobaKaijuProjectile`, `Morningstar002Projectile`, `Morningstar002ProjectileRecall`, `Morningstar002ProjectileRecallFrozenSP`, `Morningstar002UltiProjectile1`, `Morningstar002UltiProjectile2`
`Morningstar002UltiProjectile3`, `Morningstar003Projectile`, `Morningstar003ProjectileRecall`, `Morningstar003ProjectileRecallFrozenSP`, `Morningstar003UltiProjectile1`, `Morningstar003UltiProjectile2`, `Morningstar003UltiProjectile3`, `MorningstarProjectile`
`MorningstarProjectileRecall`, `MorningstarProjectileRecallFrozenSP`, `MorningstarUltiProjectile1`, `MorningstarUltiProjectile1Overcharged`, `MorningstarUltiProjectile2`, `MorningstarUltiProjectile2Overcharged`, `MorningstarUltiProjectile3`, `MorningstarUltiProjectile3Overcharged`
`MorningstarUltiProjectileOvercharged1`, `MorningstarUltiProjectileOvercharged2`, `MorningstarUltiProjectileOvercharged3`, `Mortis003UltiProjectile`, `Mortis005UltiProjectile`, `Mortis006UltiProjectile`, `Mortis007UltiProjectile`, `Mortis008AfterChargeOverchargedProjectile`
`Mortis008OverchargedUltiProjectile`, `Mortis008OverchargedUltiProjectileReturn`, `Mortis008UltiProjectile`, `Mortis009UltiProjectile`, `MosquitoProjectile`, `MosquitoProjectilePoison`, `MtowerProjectile`, `MummyAcidProjectile`
`MummyGadgetSkillAcidSprayProjectile`, `MummyGadgetSkillAcidSprayProjectileBuddy`, `MummyGadgetSkillFriendzonerProjectile`, `MummyGadgetSkillFriendzonerProjectileBuddy`, `MummyOverchargedProjectile`, `MummyProjectile`, `MummyWeaponOverchargedProjectile`, `Nani002UltiProjectile`
`Nani003Projectile`, `Nani003UltiProjectile`, `Nani004Projectile`, `Nani004UltiProjectile`, `Nani005Projectile`, `Nani005UltiProjectile`, `Nani006Projectile`, `Nani006UltiProjectile`
`Nani007Projectile`, `Nani007UltiProjectile`, `Nani008Projectile`, `Nani008UltiProjectile`, `NaniBounceProjectile`, `NaniBounceProjectileSmall`, `NaniGoldUltiProjectile`, `NaniSilverUltiProjectile`
`NanoPercenterProjectile`, `NinjaBonusSkillInvisibleAreaProjectile`, `NinjaBonusSkillInvisibleAreaProjectileBuddy`, `Otis003BigProjectile`, `Otis003Projectile`, `Otis003UltiProjectile`, `Otis004BigProjectile`, `Otis004Projectile`
`Otis004UltiProjectile`, `Otis005BigProjectile`, `Otis005Projectile`, `Otis005UltiProjectile`, `Otis006BigProjectile`, `Otis006Projectile`, `Otis006UltiProjectile`, `Otto0002UltiProjectile`
`Otto002BigProjectile`, `Otto002Projectile`, `OverchargedCrossBomberUltiProjectile`, `OverchargedCrossBomberUltiProjectile2`, `OverchargedDuplicatorProjectile`, `OverchargedDuplicatorUltiProjectile`, `OverchargedPuppeteerUltiProjectile`, `Painter002Projectile`
`Painter002UltiProjectile`, `Painter003Projectile`, `Painter003UltiProjectile`, `Painter004Projectile`, `Painter004UltiProjectile`, `Painter005Projectile`, `Painter005UltiProjectile`, `PainterProjectile`
`PainterUltiProjectile`, `Pam002Projectile`, `Pam002UltiProjectile`, `Pam003Projectile`, `Pam003UltiProjectile`, `Pam006Projectile`, `Pam006UltiProjectile`, `Pam007Projectile`
`Pam007UltiProjectile`, `Pam008Projectile`, `Pam008UltiProjectile`, `Pearl002Projectile`, `Pearl003Projectile`, `Pearl004Projectile_k2`, `Penny002Projectile`, `Penny002Projectile2`
`Penny002TurretProjectile`, `Penny002UltiProjectile`, `Penny003Projectile`, `Penny003Projectile2`, `Penny003UltiProjectile`, `Penny004Projectile`, `Penny004Projectile2`, `Penny004UltiProjectile`
`Penny005Projectile`, `Penny005Projectile2`, `Penny005TurretProjectile`, `Penny005UltiProjectile`, `Penny006Projectile`, `Penny006Projectile2`, `Penny006TurretProjectile`, `Penny006UltiProjectile`
`Penny007Projectile`, `Penny007Projectile2`, `Penny007TurretProjectile`, `Penny007UltiProjectile`, `Penny008Projectile`, `Penny008Projectile2`, `Penny008TurretProjectile`, `Penny008UltiProjectile`
`Penny009Projectile`, `Penny009Projectile2`, `Penny009TurretProjectile`, `Penny009UltiProjectile`, `PercenterCharmSkillBuddyProjectile`, `PercenterCharmSkillProjectile`, `PercenterLifestealBuddyProjectile`, `PercenterLifestealProjectile`
`PercenterOverchargedProjectile`, `PercenterOverchargedProjectileSecondary`, `PercenterProjectile`, `Piper002Projectile`, `Piper004Projectile`, `Piper005Projectile`, `Piper006Projectile`, `Piper007Projectile`
`Piper008Projectile`, `Piper009Projectile`, `Piper010OverchargedProjectile`, `Piper010Projectile`, `Piper011Projectile`, `PiperHandgunProjectile`, `Poco002Projectile`, `Poco002UltiProjectile`
`Poco003Projectile`, `Poco003UltiProjectile`, `Poco004Projectile`, `Poco004UltiProjectile`, `Poco005Projectile`, `Poco005UltiProjectile`, `Poco006Projectile`, `Poco006UltiProjectile`
`Poco007Projectile`, `Poco007UltiProjectile`, `Poco008Projectile`, `Poco008UltiProjectile`, `Poco009Projectile`, `Poco009UltiProjectile`, `Poco010OverchargedProjectile`, `Poco010OverchargedUltiProjectile`
`Poco010Projectile`, `Poco010UltiProjectile`, `PowerLevelerOverchargedProjectile`, `PowerLevelerOverchargedProjectile2`, `PowerLevelerOverchargedProjectile2Buddy`, `PowerLevelerOverchargedProjectileBuddy`, `PowerLevelerOverchargedUltiProjectile`, `PowerLevelerProjectile`
`PowerLevelerProjectile2`, `Primo003Projectile`, `Primo004Projectile`, `Primo005Projectile`, `Primo006Projectile`, `Primo007Projectile`, `Primo008Projectile`, `Primo009Projectile`
`Primo010Projectile`, `Primo011Projectile`, `Primo012Projectile`, `Primo013Projectile`, `Primo014Projectile`, `PrimoDefOverchargedProjectile`, `PrimoDefProjectile`, `Puppeteer002Projectile`
`Puppeteer002UltiProjectile`, `Puppeteer003Projectile`, `Puppeteer003UltiProjectile`, `Puppeteer004Projectile`, `Puppeteer004UltiProjectile`, `PuppeteerProjectile`, `PuppeteerUltiProjectile`, `RaidBossProjectileGold`
`RaidBossProjectileRed`, `RaidBossProjectileRedDestroyEnv`, `RaidBossRangedEnemyProjectile`, `RaidBossRocketProjectile`, `RaidBossTCBasicAttackProjectile`, `Redirecter002Projectile`, `Redirecter002ProjectileSecondary`, `Redirecter002UltiProjectile`
`RedirecterProjectile`, `RedirecterProjectileSecondary`, `RedirecterUltiProjectile`, `RedirecterUltiProjectileOvercharged`, `Reviver002UltiProjectile`, `Reviver003UltiProjectile`, `Reviver004UltiProjectile`, `Reviver005UltiProjectile`
`ReviverOverchargedUltiProjectile`, `ReviverUltiProjectile`, `Rico002Projectile`, `Rico002UltiProjectile`, `Rico003Projectile`, `Rico003UltiProjectile`, `Rico004Projectile`, `Rico004UltiProjectile`
`Rico005Projectile`, `Rico005UltiProjectile`, `Rico006Projectile`, `Rico006UltiProjectile`, `Rico007Projectile`, `Rico007UltiProjectile`, `Rico008Projectile`, `Rico008UltiProjectile`
`Rico008lOverchargedProjectile`, `Rico008lOverchargedProjectileBuddy`, `Rico008lOverchargedUltiProjectile`, `Rico009Projectile`, `Rico009UltiProjectile`, `Rico010Projectile`, `Rico010UltiProjectile`, `Rico011Projectile`
`Rico011UltiProjectile`, `RoboWarsBaseProjectile`, `RocketGirlGadgetProjectile`, `RocketGirlGadgetSkillMegaRocketProjectile`, `RocketGirlGadgetSkillMegaRocketProjectileBuddy`, `RocketGirlGadgetSplittingProjectile`, `RocketGirlProjectile`, `RocketGirlProjectileOvercharged`
`RocketGirlProjectileSecondary`, `RocketGirlProjectileSecondaryOvercharged`, `RocketGirlUltiOverchargedProjectile`, `RocketGirlUltiProjectile`, `RogueliteCirclingProjectile3`, `RogueliteCirclingProjectileClose`, `RogueliteCirclingProjectileFar`, `RogueliteLCardSqueakProjectile2`
`Roller002Projectile`, `Roller003Projectile`, `Roller004Projectile`, `Roller005Projectile`, `Roller006Projectile`, `RollerGadgetProjectile`, `RollerOverchargedProjectile`, `RollerProjectile`
`RopeDudeOverchargedUltiProjectile`, `RopeDudeProjectile`, `RopeDudeUltiProjectile`, `Rosa002Projectile`, `Rosa003Projectile`, `Rosa004Projectile`, `Rosa005Projectile`, `Rosa006Projectile`
`Rosa007Projectile`, `Rosa008Projectile`, `RosaProjectile`, `Ruffs002Projectile`, `Ruffs002UltiProjectile`, `Ruffs003Projectile`, `Ruffs003UltiProjectile`, `Ruffs004Projectile`
`Ruffs004UltiProjectile`, `Ruffs005Projectile`, `Ruffs005UltiProjectile`, `Ruffs006Projectile`, `Ruffs006UltiProjectile`, `Ruffs007Projectile`, `Ruffs007UltiProjectile`, `RuffsOverchargedUltiProjectile`
`RuffsProjectile`, `RuffsUltiProjectile`, `Samurai002UltiProjectile`, `Samurai003OverchargedUltiProjectile`, `Samurai003UltiProjectile`, `Samurai004UltiProjectile`, `SamuraiOverchargedUltiProjectile`, `SamuraiRangedEnemyProjectile`
`SamuraiUltiProjectile`, `SandstormModifierProjectile`, `SandstormOverchargedUltiProjectile`, `SandstormProjectile`, `SandstormUltiProjectile`, `Sandy002Projectile`, `Sandy002UltiProjectile`, `Sandy003Projectile`
`Sandy003UltiProjectile`, `Sandy004Projectile`, `Sandy004UltiProjectile`, `Sandy005Projectile`, `Sandy005UltiProjectile`, `Sandy006Projectile`, `Sandy006UltiProjectile`, `Sandy007Projectile`
`Sandy007UltiProjectile`, `ShadowdemonCloneBulletProjectile`, `ShadowdemonProjectileDirect`, `ShadowdemonProjectileIndirect`, `ShadowdemonUltiProjectile`, `Shaman003Projectile`, `Shaman003UltiProjectile`, `Shaman004Projectile`
`Shaman004UltiProjectile`, `Shaman005Projectile`, `Shaman005UltiProjectile`, `Shaman006Projectile`, `Shaman006UltiProjectile`, `Shaman007Projectile`, `Shaman007UltiProjectile`, `Shaman008Projectile`
`Shaman008UltiProjectile`, `Shaman009Projectile`, `Shaman009UltiProjectile`, `Shaman011Projectile`, `Shaman011UltiProjectile`, `Shaman012OverChargedProjectile`, `Shaman012OverChargedUltiProjectile`, `Shaman012Projectile`
`Shaman012UltiProjectile`, `Shaman013Projectile`, `Shaman013UltiProjectile`, `ShamanOverChargedUltiProjectile`, `ShamanOverchargedProjectile`, `ShamanProjectile`, `ShamanStarPowerProjectile`, `ShamanUltiProjectile`
`Shelly002Projectile`, `Shelly002UltiProjectile`, `Shelly003Projectile`, `Shelly003UltiProjectile`, `Shelly004Projectile`, `Shelly004UltiProjectile`, `Shelly005Projectile`, `Shelly005UltiProjectile`
`Shelly006Projectile`, `Shelly006UltiProjectile`, `Shelly007Projectile`, `Shelly007UltiProjectile`, `Shelly008Projectile`, `Shelly008UltiProjectile`, `Shelly009Projectile`, `Shelly009UltiProjectile`
`Shelly010Projectile`, `Shelly010UltiProjectile`, `ShellyOverchargedProjectile`, `ShieldTankOverchargedUltiProjectile`, `ShieldTankProjectile`, `ShieldTankUltiProjectile`, `ShotgunGirlOverchargedUltiProjectile`, `ShotgunGirlPetProjectile`
`ShotgunGirlProjectile`, `ShotgunGirlProjectileGadgetSkill`, `ShotgunGirlProjectileGadgetSkillBuddy`, `ShotgunGirlUltiProjectile`, `SignalStrikeProjectile`, `SignalStrikeProjectile_lvl3`, `SilencerBigProjectile`, `SilencerOverchargedUltiProjectile`
`SilencerProjectile`, `SilencerUltiProjectile`, `Skater002Projectile`, `Skater002ProjectileTaunt`, `Skater003Projectile`, `Skater003ProjectileTaunt`, `Skater004Projectile`, `Skater004ProjectileTaunt`
`SkaterProjectile`, `SkaterProjectileTaunt`, `SnakeOilHyperExplodedProjectile`, `SnakeOilHyperUltiProjectile`, `SnakeOilProjectile`, `SnakeOilUltiProjectile`, `SniperHomingProjectile`, `SniperProjectile`
`SoulCollectorKnockbackSoulProjectile`, `SoulCollectorKnockbackSoulProjectileBuddy`, `SoulCollectorOverchargedProjectile`, `SoulCollectorProjectile`, `SoulCollectorUltiProjectile`, `SpawnerDude002IndirectProjectile`, `SpawnerDude002Projectile`, `SpawnerDude002UltiProjectile`
`SpawnerDude003IndirectProjectile`, `SpawnerDude003Projectile`, `SpawnerDude003UltiProjectile`, `SpawnerDude004IndirectProjectile`, `SpawnerDude004Projectile`, `SpawnerDude004UltiProjectile`, `SpawnerDude005IndirectProjectile`, `SpawnerDude005Projectile`
`SpawnerDude005UltiProjectile`, `SpawnerDude006IndirectProjectile`, `SpawnerDude006Projectile`, `SpawnerDude006UltiProjectile`, `SpawnerDude007IndirectProjectile`, `SpawnerDude007Projectile`, `SpawnerDude007UltiProjectile`, `SpawnerDudeIndirectProjectile`
`SpawnerDudeMutantProjectile`, `SpawnerDudeOverchargedUltiProjectile`, `SpawnerDudeProjectile`, `SpawnerDudeUltiProjectile`, `SpawnerOverchargedPetProjectile`, `SpawnerPet002Projectile`, `SpawnerPet003Projectile`, `SpawnerPet004Projectile`
`SpawnerPet005Projectile`, `SpawnerPet006Projectile`, `SpawnerPet007Projectile`, `SpawnerPetProjectile`, `SpeedyOverchargedBuddyProjectile`, `SpeedyOverchargedProjectile`, `SpeedyProjectile`, `SpeedyRewindProjectile`
`Spike002Projectile`, `Spike002Spike`, `Spike002UltiProjectile`, `Spike003Frag`, `Spike003Projectile`, `Spike003UltiProjectile`, `Spike004Frag`, `Spike004Projectile`
`Spike004UltiProjectile`, `Spike005Frag`, `Spike005Projectile`, `Spike005UltiProjectile`, `Spike006Frag`, `Spike006Projectile`, `Spike006UltiProjectile`, `Spike007Frag`
`Spike007Projectile`, `Spike007UltiProjectile`, `Spike008Frag`, `Spike008Projectile`, `Spike008UltiProjectile`, `Spike009Frag`, `Spike009Projectile`, `Spike009UltiProjectile`
`Spike010Frag`, `Spike010Projectile`, `Spike010UltiProjectile`, `SpikeOverchargedFrag`, `SpikeOverchargedProjectile`, `Splitter002Projectile`, `Splitter004Projectile`, `Splitter005Projectile`
`SplitterCirclingProjectile`, `SplitterProjectile`, `Sprout002Projectile`, `Sprout002SecondaryProjectile`, `Sprout002UltiProjectile`, `Sprout003ChromaUltiProjectile`, `Sprout003Projectile`, `Sprout003SecondaryProjectile`
`Sprout003UltiProjectile`, `Sprout004Projectile`, `Sprout004SecondaryProjectile`, `Sprout004UltiProjectile`, `Sprout005Projectile`, `Sprout005SecondaryProjectile`, `Sprout005UltiProjectile`, `Sprout006Projectile`
`Sprout006SecondaryProjectile`, `Sprout006UltiProjectile`, `Sprout007Projectile`, `Sprout007SecondaryProjectile`, `Sprout007UltiProjectile`, `Squeak002Projectile`, `Squeak002UltiProjectile`, `Squeak002UltiProjectile2`
`Squeak003Projectile`, `Squeak003UltiProjectile`, `Squeak003UltiProjectile2`, `Squeak004Projectile`, `Squeak004UltiProjectile`, `Squeak004UltiProjectile2`, `Squeak005Projectile`, `Squeak005UltiProjectile`
`Squeak005UltiProjectile2`, `Squeak006Projectile`, `Squeak006UltiProjectile`, `Squeak006UltiProjectile2`, `Squeak007Projectile`, `Squeak007UltiProjectile`, `Squeak007UltiProjectile2`, `Squeak008Projectile`
`Squeak008UltiProjectile`, `Squeak008UltiProjectile2`, `StackerCollectProjectile`, `StackerGadgetProjectile`, `StackerProjectile`, `StackerUltiProjectile`, `StickyBombOverchargedUltiProjectile`, `StickyBombOverchargedUltiProjectile2`
`StickyBombOverchargedUltiProjectileBounce`, `StickyBombProjectile`, `StickyBombUltiProjectile`, `StickyBombUltiProjectile2`, `SuperNovaBeeSniperChargedProjectile`, `SuperNovaBeeSniperProjectile`, `SuperNovaBeeSniperUltiProjectile`, `SuperNovaCactusProjectile`
`SuperNovaCactusSpike`, `SuperNovaCactusSpikeChain`, `SuperNovaCactusSpikeCurve`, `SuperNovaCactusUltiProjectile`, `SuperNovaFireDudeProjectile`, `SuperNovaFireDudeUltiProjectile`, `SuperNovaVoodooPetProjectile`, `SuperNovaVoodooProjectileEarth`
`SuperNovaVoodooProjectileEarthChain1`, `SuperNovaVoodooProjectileEarthChain2`, `SuperNovaVoodooProjectileForest`, `SuperNovaVoodooProjectileForestChain1`, `SuperNovaVoodooProjectileForestChain2`, `SuperNovaVoodooProjectileWater`, `SuperNovaVoodooProjectileWaterChain1`, `SuperNovaVoodooProjectileWaterChain2`
`SuperNovaVoodooUltiProjectile`, `SupportArchetypeProjectile`, `Surge002Projectile`, `Surge002Projectile2`, `Surge003Projectile`, `Surge003Projectile2`, `Surge004Projectile`, `Surge004Projectile2`
`Surge005Projectile`, `Surge005Projectile2`, `Surge006Projectile`, `Surge006Projectile2`, `Surge007Projectile`, `Surge007Projectile2`, `Surge008Projectile`, `Surge008Projectile2`
`Surge010Projectile2_k2`, `Surge010Projectile_k2`, `Surge011Projectile`, `Surge011Projectile2`, `Tara002Projectile`, `Tara002UltiProjectile`, `Tara003Projectile`, `Tara003UltiProjectile`
`Tara004Projectile`, `Tara004UltiProjectile`, `Tara005Projectile`, `Tara005UltiProjectile`, `Tara006Projectile`, `Tara006UltiProjectile`, `Tara007Projectile`, `Tara007UltiProjectile`
`Tara008Projectile`, `Tara008UltiProjectile`, `Tick002Projectile`, `Tick002Projectile2`, `Tick002UltiProjectile`, `Tick003Projectile`, `Tick003Projectile2`, `Tick003UltiProjectile`
`Tick004Projectile`, `Tick004Projectile2`, `Tick004UltiProjectile`, `Tick005Projectile`, `Tick005Projectile2`, `Tick005UltiProjectile`, `Tick006Projectile`, `Tick006Projectile2`
`Tick006UltiProjectile`, `Tick007Projectile`, `Tick007Projectile2`, `Tick007UltiProjectile`, `Tick008UltiProjectile`, `Tick009Projectile`, `Tick009Projectile2`, `Tick009UltiProjectile`
`Tick010Projectile`, `Tick010Projectile2`, `Tick010UltiProjectile`, `TickGoldUltiProjectile`, `TickSilverUltiProjectile`, `TntDudeChefProjectile`, `TntDudeChefUltiProjectile`, `TntDudeNanoChainProjectile`
`TntDudeOverchargedClusterProjectile`, `TntDudeOverchargedUltiProjectile`, `TntDudeProjectile`, `TntDudeSantaProjectile`, `TntDudeSantaUltiProjectile`, `TntDudeUltiProjectile`, `TrickShotGadgetSkillContainerProjectile`, `TrickShotGadgetSkillContainerProjectileBuddy`
`TrickshotDudeGadgetProjectile`, `TrickshotDudeGadgetSkillProjectile`, `TrickshotDudeGadgetSkillProjectileBuddy`, `TrickshotDudeGadgetSkillSplitterShotProjectile`, `TrickshotDudeGadgetSkillSplitterShotProjectile2`, `TrickshotDudeGadgetSkillSplitterShotProjectileBuddy`, `TrickshotDudeNanoProjectile`, `TrickshotDudeProjectile`
`TrickshotDudeProjectileBigBulletSplit`, `TrickshotDudeProjectileBigBulletSplitBuddy`, `TrickshotDudeProjectileOverchargeBuddy`, `TrickshotDudeUltiOverchargedProjectile`, `TrickshotDudeUltiProjectile`, `Turret003Proj`, `Turret003Proj2`, `Turret003Proj3`
`Turret004Proj`, `Turret004Proj2`, `Turret004Proj3`, `Turret005Proj`, `Turret005Proj2`, `Turret005Proj3`, `Turret006Proj`, `Turret006Proj2`
`Turret006Proj3`, `Turret007Proj`, `Turret007Proj2`, `Turret007Proj3`, `Turret008Proj`, `Turret008Proj2`, `Turret008Proj3`, `Turret009Proj`
`Turret009Proj2`, `Turret009Proj3`, `Turret010Proj`, `Turret010Proj2`, `Turret010Proj3`, `Turret011Proj`, `Turret011Proj2`, `Turret011Proj3`
`TurretElecProj`, `TurretElecProj2`, `TurretElecProj3`, `TurretWaterProj`, `TurretWaterProj2`, `TurretWaterProj3`, `Twins002ShotgunProjectile`, `Twins002ThrowerProjectile`
`Twins002UltiProjectile`, `Twins003ShotgunProjectile`, `Twins003ThrowerProjectile`, `Twins003UltiProjectile`, `Twins004ShotgunProjectile`, `Twins004ThrowerProjectile`, `Twins004UltiProjectile`, `TwinsHCUltiProjectile`
`TwinsShotgunProjectile`, `TwinsThrowerProjectile`, `TwinsUltiProjectile`, `UndertakerAfterChargeOverchargedProjectile`, `UndertakerGadgetSkillBatsProjectile`, `UndertakerGadgetSkillBatsProjectileBuddy`, `UndertakerGadgetSkillComboSpinnerProjectile`, `UndertakerGadgetSkillComboSpinnerProjectileBuddy`
`UndertakerOverchargedUltiProjectile`, `UndertakerOverchargedUltiProjectileReturn`, `UndertakerStarPowerProjectile`, `UndertakerUltiProjectile`, `Voodoo002PetProjectile`, `Voodoo002PetSlowProjectile`, `Voodoo002ProjectileAll`, `Voodoo002ProjectileEarth`
`Voodoo002ProjectileForest`, `Voodoo002ProjectileWater`, `Voodoo002UltiProjectile`, `Voodoo003PetProjectile`, `Voodoo003PetSlowProjectile`, `Voodoo003ProjectileAll`, `Voodoo003ProjectileEarth`, `Voodoo003ProjectileForest`
`Voodoo003ProjectileWater`, `Voodoo003UltiProjectile`, `VoodooOverchargedPetSlowProjectile`, `VoodooOverchargedUltiProjectile`, `VoodooPetOverchargedProjectile`, `VoodooPetProjectile`, `VoodooPetSlowProjectile`, `VoodooProjectileAll`
`VoodooProjectileEarth`, `VoodooProjectileForest`, `VoodooProjectileWater`, `VoodooUltiProjectile`, `WallyOverchargedUltiProjectile`, `WallyProjectile`, `WallySecondaryProjectile`, `WallyUltiProjectile`
`WeaponThrowerOverchargedUltiProjectile`, `WeaponThrowerOverchargedUltiProjectile2`, `WeaponThrowerProjectile`, `WeaponThrowerProjectile2`, `WeaponThrowerUltiProjectile`, `WeaponThrowerUltiProjectile2`, `WhirlwindProjectile`, `WhirlwindProjectile2`
`WrathOfAnAngelProjectile`, `hank002UltiProjectile`, `hank003UltiProjectile`, `hank004UltiProjectile`, `hank005UltiProjectile`, `hankOverchargedUltiProjectile`

## 10. Гаджеты (`lookup(50, ...)`) и спреи (`lookup(68, ...)`)

`Alternator_DamageMode`, `Alternator_SlowMode`, `Ambusher_ShadowRealm`, `Ambusher_TeleportGrenade`, `Arcade_Double`, `Arcade_Double_Buddy`, `Arcade_Teleport`
`Arcade_Teleport_Buddy`, `ArtilleryDude_Barrage`, `ArtilleryDude_Cover`, `AssaultShotgun_Bomb`, `AssaultShotgun_Bomb_Buddy`, `AssaultShotgun_Projectiles`, `AssaultShotgun_Projectiles_Buddy`
`Attacher_Cardboardbox`, `Attacher_Cheeseburger`, `Attractor_Grounded`, `Attractor_Pushback`, `AxeJuggler_ProjectileSpeed`, `AxeJuggler_Shield`, `Barkeep_HealPotion`
`Barkeep_Slow`, `BarrelBot_Slow`, `BarrelBot_Spin`, `Baseball_Heal`, `Baseball_Heal_Buddy`, `Baseball_Proto`, `Baseball_Sticky`
`Baseball_Sticky_Buddy`, `Beamer_Pierce`, `Beamer_Slow`, `BeeSniper_ExtraBee`, `BeeSniper_Slow`, `BlackHole_Shadows`, `BlackHole_Vision`
`Blower_Stopper`, `Blower_Trampoline`, `BowDude_MineTrigger`, `BowDude_MineTrigger_Buddy`, `BowDude_Totem`, `BowDude_Totem_Buddy`, `BullDudeGadgetSkillMarkEnemy`
`BullDudeGadgetSkillMarkEnemyBuddy`, `BullDude_Stomp`, `BullDude_Stomp_Buddy`, `Bulletstorm_AbsorbShellsShieldPushback`, `Bulletstorm_Reload`, `Cactus_Cover`, `Cactus_Cover_Buddy`
`Cactus_ShootAround`, `Cactus_ShootAround_Buddy`, `CannonGirl_Dash`, `CannonGirl_Speed`, `Chronomancer_ProjectileStasis`, `Chronomancer_Time`, `ClusterBombDude_Explosion`
`ClusterBombDude_ExtraMines`, `Cocooner_CocoonSelf`, `Cocooner_SpawnPets`, `Conductor_PassWalls`, `Conductor_PassWalls_Buddy`, `Conductor_RemoveSign`, `Conductor_RemoveSign_Buddy`
`Controller_BounceBack`, `Controller_Explode`, `Cooker_Healing`, `Cooker_Poison`, `Crab_Dash`, `Crab_DoubleTokens`, `CrossBomber_Burst`
`CrossBomber_Vision`, `Crow_InstaDot_Buddy`, `Crow_PoisonDagger`, `Crow_PoisonDagger_Buddy`, `Crow_Shield`, `Dancer_BlockProjectiles`, `Dancer_RechargeUlti`
`Daredevil_Area`, `Daredevil_Hide`, `DeadMariachi_Cleanse`, `DeadMariachi_Cleanse_Buddy`, `DeadMariachi_Regen`, `DeadMariachi_Regen_Buddy`, `Digger_Dash`
`Digger_Treasure`, `Domain_Area`, `Domain_InverseDamage`, `DoorMan_DamageDrop`, `DoorMan_Puller`, `DragonRider_KnockUp`, `DragonRider_LastStand`
`Driller_Proto`, `Driller_Rebuild`, `Driller_SpeedBoost`, `Duelist_Jump`, `Duelist_Silence`, `Duplicator_StaticDuplicate`, `Duplicator_Swap`
`ElectroSniper_Bounce`, `ElectroSniper_Trap`, `Enrager_Gadget_LetsFly`, `Enrager_Gadget_LetsFly_Buddy`, `Enrager_Protection`, `Enrager_Protection_Buddy`, `Enrager_SuperBoost`
`FireDude_FlameShield`, `FireDude_FlameShield_Buddy`, `FireDude_Spill`, `FireDude_Spill_Buddy`, `FishTank_Shield`, `FishTank_Slow`, `Flea_Jump`
`Flea_Symbiosis`, `Fury_FakeAttack`, `Fury_Teleport`, `FutureGirl_Leap`, `FutureGirl_ProjectileGadget`, `Geisha_Gadget_0`, `Geisha_Gadget_1`
`Geisha_Gadget_2`, `Ghost_IncreasedRange`, `Ghost_IncreasedRange_Buddy`, `Ghost_Spooky`, `Ghost_Spooky_Buddy`, `Gladiator_Amp`, `Gladiator_Wall`
`Gunslinger_BigBullet`, `Gunslinger_BigBullet_Buddy`, `Gunslinger_Reload`, `Gunslinger_Reload_Buddy`, `HammerDude_Immunity`, `HammerDude_Immunity_Buddy`, `HammerDude_Pull`
`HammerDude_Pull_Buddy`, `HookDude_Homing`, `HookDude_Push`, `IceDude_AreaFreeze`, `IceDude_Freeze`, `InsectMan_Fly`, `InsectMan_Pierce`
`Jester_RandomBuff`, `Jester_ReRollUlti`, `JetpackGirl_DamageTower`, `JetpackGirl_JumpAttack`, `KatanaKid_FishNet`, `KatanaKid_HealFish`, `KickerDude_Mines`
`KickerDude_Sweep`, `Knight_Heal`, `Knight_Rage`, `Leaper_LongerJump`, `Leaper_Shotgun`, `Lightyear_Accessory`, `Luchador_Grab`
`Luchador_Grab_Buddy`, `Luchador_Meteor`, `Luchador_Meteor_Buddy`, `MagicalGirl_FlyArea`, `MagicalGirl_Healing`, `Maisie_Dash`, `Maisie_ReloadAndDamage`
`MechaDude_Buddy_Heal`, `MechaDude_Buddy_Toolbox`, `MechaDude_Heal`, `MechaDude_ReloadTower`, `Mechanic_Slow`, `Mechanic_TurretBuff`, `Meeple_RageQuit`
`Meeple_WallAttack`, `Mender_DashHeal`, `Mender_SuperchargeTethers`, `MinigunDude_AmmoSink`, `MinigunDude_BurstHeal`, `Morningstar_Fire`, `Morningstar_Ice`
`Mummy_Acid`, `Mummy_Acid_Buddy`, `Mummy_Push`, `Mummy_Push_Buddy`, `Ninja_Fake`, `Ninja_Fake_Buddy`, `Ninja_InvisibleArea`
`Ninja_InvisibleArea_Buddy`, `Painter_AreaDuration`, `Painter_Push`, `Percenter_CharmAttack`, `Percenter_CharmAttack_Buddy`, `Percenter_Lifesteal`, `Percenter_Lifesteal_Buddy`
`Percenter_StaticDamage`, `PowerLeveler_Blink`, `PowerLeveler_ExtraLevels`, `PowerLeveler_ExtraLevels_Buddy`, `PowerLeveler_Shield`, `PowerLeveler_Shield_Buddy`, `Puppeteer_Dive`
`Puppeteer_MoreDamage`, `Redirecter_CocoonSelf`, `Redirecter_PoisonTrail`, `Reviver_OnlyDoubleDamage`, `Reviver_OnlyDoubleHeal`, `Rock_Jump`, `Rock_Shield`
`RocketGirl_Jump`, `RocketGirl_Jump_Buddy`, `RocketGirl_MegaRocket`, `RocketGirl_MegaRocket_Buddy`, `Roller_MegaStunt`, `Roller_Speed`, `RopeDude_Vision`
`RopeDude_WeakUlti`, `Rosa_BushControl`, `Rosa_GrowBush`, `Ruffs_AirStrike`, `Ruffs_Cover`, `Samurai_HealDamageTaken`, `Samurai_OneAttackOnly`
`Sandstorm_Sleep`, `Sandstorm_StunSleep`, `Shadowdemon_CloneBullet`, `Shadowdemon_Recall`, `Shaman_PetSlam`, `Shaman_PetSlam_Buddy`, `Shaman_Shield`
`Shaman_Shield_Buddy`, `ShieldTank_Heal`, `ShieldTank_Pull`, `ShotgunGirl_Dash`, `ShotgunGirl_Dash_Buddy`, `ShotgunGirl_Focus`, `ShotgunGirl_Focus_Buddy`
`Silencer_BigProjectiles`, `Silencer_Mine`, `Skater_Jump`, `Skater_ProjectileTaunt`, `SnakeOil_Heal`, `SnakeOil_Spread`, `Sniper_HandGun`
`Sniper_Seeker`, `SoulCollector_ExplodeSouls`, `SoulCollector_KnockbackSoul`, `SoulCollector_KnockbackSoulBuddy`, `SpawnerDude_ExtraPorter`, `SpawnerDude_Promote`, `Speedy_Dash`
`Speedy_Dash_Buddy`, `Speedy_Rewind`, `Splitter_ChargeUlti`, `Splitter_TriggerTags`, `Stacker_Accessory_1`, `Stacker_Accessory_2`, `Stalker_BloodhuntOverride`
`Stalker_Lifesteal`, `StickyBomb_Range`, `StickyBomb_Vision`, `TntDude_Spin`, `TntDude_Stun`, `TrickshotDude_BounceHeal`, `TrickshotDude_BounceHealBuddy`
`TrickshotDude_ShootAround`, `TrickshotDude_ShootAroundBuddy`, `Twins_Dash`, `Twins_SwapSkill`, `Undertaker_Reload`, `Undertaker_Reload_Buddy`, `Undertaker_Swing`
`Undertaker_Swing_Buddy`, `Voodoo_AllBuffsAttack`, `Voodoo_SelfBuff`, `Wally_Heal`, `Wally_Reposition`, `WeaponThrower_Explode`, `WeaponThrower_Pull`
`Whirlwind_Fly`, `Whirlwind_Trail`


Спреи (для `item.sprayDataIndex` — индекс спрея задаётся числом, не именем):

`spray_26wf_cr`, `spray_26wf_fnl`, `spray_26wf_fut`, `spray_26wf_hmb`, `spray_26wf_loud`, `spray_26wf_navi`, `spray_26wf_sk`, `spray_26wf_th`
`spray_26wf_totem`, `spray_26wf_tribe`, `spray_26wf_zeta`, `spray_8bit_1`, `spray_8bit_enchanted`, `spray_8bit_sandsoftime`, `spray_8bit_virus`, `spray_8bit_virus_og`
`spray_allfine`, `spray_alli`, `spray_allie_brawlentine`, `spray_amazon_frog`, `spray_amber_1`, `spray_amber_ice`, `spray_angel_door`, `spray_angel_helmet`
`spray_angel_wing`, `spray_angeldemon_fanfare`, `spray_angeldemon_pet`, `spray_angelo`, `spray_angelsdemons_1`, `spray_angelsdemons_2`, `spray_angelsdemons_3`, `spray_angelsdemons_4`
`spray_angrycloud`, `spray_anime_book`, `spray_anime_bow`, `spray_anime_gem`, `spray_anime_icecream`, `spray_anime_itisokay`, `spray_anime_moon`, `spray_anime_smash`
`spray_anime_starrnova`, `spray_anime_thumbdown`, `spray_anniversary1`, `spray_anniversary2`, `spray_aprilfool_balloons`, `spray_aprilfools_stare`, `spray_ash_1`, `spray_badgem`
`spray_badrandoms`, `spray_banana`, `spray_barley_1`, `spray_bea_1`, `spray_belle_1`, `spray_belle_fantasy`, `spray_berry`, `spray_bibi_1`
`spray_bibi_bt21`, `spray_bibi_cursed`, `spray_bibi_ragnarok`, `spray_bibi_virus`, `spray_bling`, `spray_bo_1`, `spray_bo_hindu`, `spray_bo_mecha`
`spray_bolt_1`, `spray_bolt_2`, `spray_bolt_3`, `spray_bonnie_1`, `spray_bounty`, `spray_box_bolt`, `spray_box_cosmo`, `spray_box_damian`
`spray_box_gigi`, `spray_box_glowbert`, `spray_box_lvl_3`, `spray_box_lvl_4`, `spray_box_mina`, `spray_box_najia`, `spray_box_nori`, `spray_box_pierce`
`spray_box_sirius`, `spray_box_stella`, `spray_box_vince`, `spray_box_wendy`, `spray_box_ziggy`, `spray_bp_angelsdemons`, `spray_bp_anime`, `spray_bp_brawloween25`
`spray_bp_brawloween26`, `spray_bp_darkonce`, `spray_bp_darksands`, `spray_bp_deepsea`, `spray_bp_deepsea-extra1`, `spray_bp_deepsea-extra2`, `spray_bp_dragon`, `spray_bp_fantasybo`
`spray_bp_feudaljapan`, `spray_bp_godzilla`, `spray_bp_goodrandoms`, `spray_bp_greekmortis`, `spray_bp_hackers`, `spray_bp_kaiju`, `spray_bp_mecha`, `spray_bp_nano`
`spray_bp_olympic`, `spray_bp_sandsoftime26`, `spray_bp_sb`, `spray_bp_st`, `spray_bp_starrforce`, `spray_bp_steampunk`, `spray_bp_street`, `spray_bp_strikers`
`spray_bp_super`, `spray_bp_toons2`, `spray_bp_university26`, `spray_bp_valentines25`, `spray_bp_windstock`, `spray_brawlentine_2024_1`, `spray_brawlentine_2024_2`, `spray_brawlentine_cure`

## 11. Роботы, боссы, миньоны, турели и петы (тип 16)

Имена для `lookup(16, "Имя")` из `characters.csv`. В колонке `Type` указана роль объекта в бою.
Всего в `characters.csv` **435** объектов: **122** бойцов (`Hero`) и **313** объектов окружения — роботы, боссы, турели, петы, мины, вагонетки, базы.

### 11.1 Быстрая шпаргалка: кто чей

Последняя колонка — на чём основана привязка: **CSV** = ссылка из колонок `Pet`/`AltPet`/`BuddyCharacter`/`ExtraMinions` или имя скина; **префикс** = владелец определён по совпадению начала имени (в CSV явной ссылки нет).

| Объект | `lookup(16, ...)` | Тип | Основание |
|---|---|---|---|
| Медведь Ниты | `ShamanPet` | Minion_FindEnemies | скин `ShamanBearDefault` (Shaman = nita) |
| Турель Джесси | `MechanicTurret` | Minion_Building | префикс (Mechanic = jessie) |
| Артиллерия (мортира) Пенни | `ArtilleryDudeTurret` | Minion_Building | префикс (ArtilleryDude = penny) |
| Ящик-укрытие Пенни | `ArtilleryDudeCover` | Minion_Building | префикс (ArtilleryDude = penny) |
| Станция лечения Пэм | `HealingStation` | Minion_Building | префикс + AreaEffect `HealingStationHeal` (pam) |
| Усиленная станция Пэм | `OverchargedHealingStation` | Minion_Building | CSV: `AltPet` у HealingStation |
| Тотем Бо (заряжает суперы) | `BowDudeTotem` | Minion_Building | AreaEffect `BowDudeSuperChargeArea` (BowDude = bo) |
| Яйцо Евы | `FleaBigEgg` | Minion_Building | префикс (Flea = eve) |
| Питомец Динамайка | `TntPet` | Minion_FollowOwner | CSV: `Pet` у TntDude / dynamike |
| Кокон Чарли | `CocoonerCocoon` | Minion_Building | префикс (Cocooner = charlie) |
| Турель Венди | `FutureGirlTurret` | Minion_Building | префикс (FutureGirl = wendy) |
| База портеров Мистера П. | `SpawnerDudeTurret` | Minion_Building | префикс (SpawnerDude = mr.p) |
| Башня перезарядки Мег | `MechaDudeReloadTower` | Minion_Building | префикс (MechaDude = meg) |
| Пушечная вышка Джанет | `JetpackGirlDamageTower` | Minion_Building | префикс (JetpackGirl = janet) |
| Обманка Леона | `NinjaFake` | Minion_Mirage | префикс (Ninja = leon), тип `Minion_Mirage` |
| Двойник Лолы | `DuplicatorPet` | Minion_Duplicate | префикс (Duplicator = lolla) |
| Двойник близнецов | `TwinsPet` | Minion_Twin | CSV: `Pet` у Twins / twins |
| Горшок-замедление Беи | `BeeSniperSlowPot` | Minion_Building | CSV: `Pet` у BeeSniper / bea |
| Черная дыра Тары | `BlackHolePet` | Minion_FindEnemies | CSV: `Pet` у BlackHole / tara |
| Бочка-взрывчатка (окружение) | `ExplodingBarrel` | Minion_Building | элемент карты |
| Сейф (режим «Сейф») | `Safe` | Pvp_Base | база режима (`Pvp_Base`) |
| Робот-войны: база / робот / ящик | `RoboWarsBase / RoboWarsRobo / RoboWarsBox` | Pvp_Base | типы `Pvp_Base` / `RoboWars` / `LootBox` |
| Тренировочный манекен (заряжает супер) | `TrainingDummyBig` | Minion_Building_charges_ulti | тип `Minion_Building_charges_ulti` |
| Обычная пчела (владелец в CSV не указан) | `Bee` | Minion_FollowOwner | тип `Minion_FollowOwner`, ссылок нет |

### 11.2 Питомцы и напарники с подтверждением из CSV (`Pet` / `AltPet` / `BuddyCharacter` / `ExtraMinions`)

| Объект | Тип | Владелец (код / игра) |
|---|---|---|
| `ArcadeBuddy` | Minion_FindEnemies | `Arcade` / 8bit |
| `AssaultShotgunBuddy` | Minion_FindEnemies | `AssaultShotgun` / griff |
| `BaseballBuddy` | Minion_FindEnemies | `Baseball` / bibi |
| `BeeSniperSlowPot` | Minion_Building | `BeeSniper` / bea, `SuperNovaBeeSniper` / — |
| `BlackHolePet` | Minion_FindEnemies | `BlackHole` / tara |
| `BowDudeBuddy` | Minion_FindEnemies | `BowDude` / bo |
| `BullBuddy` | Minion_FindEnemies | `BullDude` / bull |
| `CactusBuddy` | Minion_FindEnemies | `Cactus` / spike |
| `CannonGirlSmall` | Hero | `CannonGirl` / bonnie |
| `CocoonerPet` | Minion_FindEnemies | `Cocooner` / charlie |
| `CrowBuddy` | Minion_FindEnemies | `Crow` / crow |
| `DiggerDrill` | Hero | `Digger` / digger |
| `EnragerBuddy` | Minion_FindEnemies | `Enrager` / edgar |
| `GeishaTransformed` | Hero | `Geisha` / kaze |
| `GunslingerBuddy` | Minion_FindEnemies | `Gunslinger` / colt |
| `HammerDudeBuddy` | Minion_FindEnemies | `HammerDude` / frank |
| `MechaDudeBig` | Hero | `MechaDude` / meg |
| `MechaDudeBuddy` | Minion_FindEnemies | `MechaDude` / meg |
| `MummyBuddy` | Minion_FindEnemies | `Mummy` / emz |
| `NinjaBuddy` | Minion_FindEnemies | `Ninja` / leon |
| `PercenterBuddy` | Minion_FindEnemies | `Percenter` / colette |
| `PercenterPet` | Minion_Percenter | `Percenter` / colette |
| `PowerLevelerBuddy` | Minion_FindEnemies | `PowerLeveler` / surge |
| `RocketGirlBuddy` | Minion_FindEnemies | `RocketGirl` / brock |
| `ShamanBuddy` | Minion_FindEnemies | `Shaman` / nita |
| `ShotgunGirlBuddy` | Minion_FindEnemies | `037424c2385e031824f496c787e2ab8f473b70f8` / shelly, `07220d24fa2e06c356cad4e7c6037d70b265010e` / shelly, `4028aae4a6bbbdea17608222005fefc028ff7c45` / shelly, `49c039b18c82880638cd3ba472dc5db3e8cc6f8b` / shelly, `4f7b8a8fb970bd4cb356d59fd76bb5fb64e5797a` / shelly, `ShotgunGirl` / shelly, `f12191a373cbc743d1f7554b27999006a017d2eb` / shelly |
| `SpeedyBuddy` | Minion_FindEnemies | `Speedy` / max |
| `SplitterLegs` | Minion_Building | `Splitter` / artie |
| `TntPet` | Minion_FollowOwner | `TntDude` / dynamike |
| `TrickshotDudeBuddy` | Minion_FindEnemies | `TrickshotDude` / ricochet |
| `TwinsPet` | Minion_Twin | `Twins` / twins |
| `UndertakerBuddy` | Minion_FindEnemies | `Undertaker` / mortis |

### 11.3 Роботы-противники (co-op, рейд, invasion, extraction)

**Боссы (`Npc_Boss`, 6):**

- `BossRaceBoss`, `CoopBoss1`, `CoopBoss2`, `CoopBoss3`
- `RaidBoss`, `SamuraiBoss`

`RaidBoss` — босс-робот рейда; `RaidBoss_TownCrush` — версия для «Таун Краш» (тип `Npc_Boss_TownCrush`).

**Миньоны рейд-боссов (`RaidBoss*`, 12):**

- `RaidBossFastMeleeEnemy1`, `RaidBossFastMeleeEnemy2`, `RaidBossFastMeleeEnemy3`, `RaidBossFastMeleeEnemy4`
- `RaidBossMeleeEnemy1`, `RaidBossMeleeEnemy2`, `RaidBossMeleeEnemy3`, `RaidBossMeleeEnemy4`
- `RaidBossRangedEnemy1`, `RaidBossRangedEnemy2`, `RaidBossRangedEnemy3`, `RaidBossRangedEnemy4`

**Миньоны co-op (`Coop*`, 12)** — `CoopMeleeEnemy1…4` (ближний бой), `CoopFastMeleeEnemy1…4` (быстрые ближники), `CoopRangedEnemy1…4` (стрелки):

- `CoopFastMeleeEnemy1`, `CoopFastMeleeEnemy2`, `CoopFastMeleeEnemy3`, `CoopFastMeleeEnemy4`
- `CoopMeleeEnemy1`, `CoopMeleeEnemy2`, `CoopMeleeEnemy3`, `CoopMeleeEnemy4`
- `CoopRangedEnemy1`, `CoopRangedEnemy2`, `CoopRangedEnemy3`, `CoopRangedEnemy4`

**Invasion / Extraction / Samurai / боты (`Minion_Invasion`, 18):**

- `BossBot`, `ExtractionFastMeleeEnemy`, `ExtractionMeleeEnemy`, `ExtractionRangedEnemy`
- `InvasionBossEnemy`, `InvasionFastMeleeEnemy`, `InvasionMeleeEnemy`, `InvasionRangedEnemy`
- `MeleeBot`, `MeleeFastBot`, `NanoDeliveryBot`, `RangedBot`
- `SamuraiFastMeleeEnemy`, `ShadowSmashSpider`, `SwarmSamuraiFastMeleeEnemy`, `SwarmSamuraiMeleeEnemy`
- `SwarmSamuraiMeleeMiniBossEnemy`, `SwarmSamuraiRangedEnemy`

Стрелковый робот — `RangedBot`, ближние — `MeleeBot` / `MeleeFastBot`, босс — `BossBot`. Ещё противники: `SwarmHunterEnemy` (`Minion_Swarm_Hunter`), `LastStandMinion` (`Minion_LastStand`), `ShadowSmashSpider`.

**Мегабоссы (`Mega_Boss`, 52)** — мега-версии бойцов и боссы событий:

- `MechaVanBossMeleeNinja`, `MechaVanBossSniper`, `MechaVanBossTank`, `MechaVanFriendlyMegBoss`
- `MechaVanMiniMeleeNinja`, `MechaVanMiniSniper`, `MechaVanMiniTank`, `MegaBossBearWithNitaCustom`
- `MegaBossBlackhole`, `MegaBossChronomancerL1`, `MegaBossChronomancerL2`, `MegaBossClusterBomb`
- `MegaBossCrow`, `MegaBossCrowDragonL1`, `MegaBossCrowDragonL2`, `MegaBossCrowDragonL3`
- `MegaBossCrowDragonL3Ghost1`, `MegaBossCrowRed`, `MegaBossCrowWhite`, `MegaBossEmz`
- `MegaBossFang`, `MegaBossFixStasisTower`, `MegaBossFixStasisTowerSecond`, `MegaBossFrank`
- `MegaBossGhost`, `MegaBossGriff`, `MegaBossGrom`, `MegaBossInsectMan`
- `MegaBossKatanaKid`, `MegaBossKatanaKid_FishSpawner1`, `MegaBossKatanaKid_FishSpawner2`, `MegaBossKenji`
- `MegaBossKenjiGhost`, `MegaBossMaisie`, `MegaBossNitaWithBearCustom`, `MegaBossPercenter`
- `MegaBossPercenterTurret`, `MegaBossRocketGirlL1`, `MegaBossRocketGirlL2`, `MegaBossRocketGirlL3`
- `MegaBossSTDg`, `MegaBossSTVec`, `MegaBossSpike`, `MegaBossSplitter`
- `MegaBossSplitterHead`, `MegaBossStickyBomb`, `MegaBossTrickshot`, `MegaBossTrickshotBrawlentines`
- `MegaBossTrickshotBrawlentines2`, `MegaBossTrickshotBrawlentines3`, `NanoGuardRanged`, `NanoGuardTank`

### 11.4 Турели, пушки и постройки (`Minion_Building`, 42)

- `ArtilleryDudeCover`, `ArtilleryDudeTurret`, `AssaultShotgunBombBuddy`, `BeeSniperSlowPot`
- `BowDudeTotem`, `BowDudeTotemBuddy`, `CactusCover`, `CactusCoverBuddy`
- `CactusCoverNanoFake`, `CocoonerCocoon`, `CrossBomberVisionTower`, `DamageBooster`
- `DamageBoosterOvercharge`, `ExplodingBarrel`, `ExplodingTank`, `FleaBigEgg`
- `FleaOverchargedBigEgg`, `FutureGirlTurret`, `HealingStation`, `HighlightEnvironment`
- `JetpackGirlDamageTower`, `MagicalGirlFlyArea`, `MechaDudeReloadTower`, `MechanicTurret`
- `MegaBossCactusCover`, `NinjaInvisibleArea`, `NinjaInvisibleAreaBuddy`, `OverchargedHealingStation`
- `OverchargedSpawnerDudeTurret`, `PoisonBarrel`, `RedirecterCocoon`, `RuffsCover`
- `SpawnerDudeTurret`, `SpawnerDudeTurret002`, `SpawnerDudeTurret003`, `SpeedBooster`
- `SplitterLegs`, `StuDrums`, `TrickshotDudeGadgetSkillContainer`, `TrickshotDudeGadgetSkillContainerBuddy`
- `TutorialDummy`, `TutorialExplodingBarrel`

**Манекены, заряжающие супер (`Minion_Building_charges_ulti`, 6):**

- `TrainingDummyBig`, `TrainingDummyMedium`, `TrainingDummyShooting`, `TrainingDummySmall`
- `TutorialDummy2`, `TutorialDummy3`

### 11.5 Петы и миньоны бойцов (`Minion_FindEnemies`, 97)

- `AngelicPet`, `AngelicPetBig`, `ArcadeBuddy`, `AssaultShotgunBuddy`
- `BaseballBuddy`, `BlackHolePet`, `BlackHolePet2`, `BlackHolePetGadget`
- `BossMinionST`, `BowDudeBuddy`, `BullBuddy`, `CactusBuddy`
- `ClusterBombPet`, `CocoonerPet`, `CoopFastMeleeEnemy1`, `CoopFastMeleeEnemy2`
- `CoopFastMeleeEnemy3`, `CoopFastMeleeEnemy4`, `CoopMeleeEnemy1`, `CoopMeleeEnemy2`
- `CoopMeleeEnemy3`, `CoopMeleeEnemy4`, `CoopRangedEnemy1`, `CoopRangedEnemy2`
- `CoopRangedEnemy3`, `CoopRangedEnemy4`, `CrowBuddy`, `DemonicPet`
- `EnragerBuddy`, `FleaExtraPet`, `FleaHealingPet`, `FleaPet`
- `GunslingerBuddy`, `HammerDudeBuddy`, `KnightPet`, `MechaDudeBuddy`
- `MechaVanFodderBomb`, `MechaVanFodderMelee`, `MechaVanFodderRanged`, `MegaBossBlackHoleExplodePet`
- `MegaBossBlackHoleShieldPet`, `MegaBossClusterBombPetBig`, `MegaBossClusterBombPetMid`, `MegaBossClusterBombPetSmall`
- `MegaBossFinxKitten`, `MegaBossGromRatPet`, `MegaBossMaisieTurret`, `MegaBossPercenterPet`
- `MegaBossShamanPet`, `MegaFrankMeleeEnemy`, `MegaKenjiPet`, `MegaSamuraiMeleeEnemy`
- `MegaSamuraiRangedEnemy`, `MegaSplitterTwinsEnemyShoot`, `MegaSplitterTwinsEnemyThrow`, `MummyBuddy`
- `NanoGuardBomb`, `NanoGuardFodderMelee`, `NanoGuardFodderRanged`, `NanoGuardMelee`
- `NinjaBuddy`, `NinjaMutation`, `NinjaNanoPowerClone`, `OverchargedRedirecterSnakePet`
- `OverchargedSpawnerPet`, `PercenterBuddy`, `PowerLevelerBuddy`, `RaidBossFastMeleeEnemy1`
- `RaidBossFastMeleeEnemy2`, `RaidBossFastMeleeEnemy3`, `RaidBossFastMeleeEnemy4`, `RaidBossMeleeEnemy1`
- `RaidBossMeleeEnemy2`, `RaidBossMeleeEnemy3`, `RaidBossMeleeEnemy4`, `RaidBossRangedEnemy1`
- `RaidBossRangedEnemy2`, `RaidBossRangedEnemy3`, `RaidBossRangedEnemy4`, `RedirecterSnakePet`
- `RocketGirlBuddy`, `SamuraiMeleeEnemy`, `SamuraiRangedEnemy`, `ShamanBuddy`
- `ShamanPet`, `ShotgunGirlBuddy`, `SpawnerPet`, `SpawnerPet002`
- `SpawnerPet003`, `SpawnerPetGadget`, `SpeedyBuddy`, `SubwayGuard`
- `SuperNovaCactusCover`, `SuperNovaVoodooPet`, `TrickshotDudeBuddy`, `UndertakerBuddy`
- `VoodooPet`

Малые группы миньонов:

- **Minion_FollowOwner:** `TntPet`, `Bee`, `ControllerAddon`, `MechaDudeAddon`, `Starfish`
- **Minion_Dog:** `BoneThrowerPet`
- **Minion_Duplicate:** `DuplicatorPet`, `OverchargedDuplicatorPet`
- **Minion_Mirage:** `NinjaFake`
- **Minion_Twin:** `TwinsPet`, `TwinsPetHyper`
- **Minion_Percenter:** `PercenterPet`
- **Minion_Orbiting:** `TankArchetypeCover`
- **Minion_Goalkeeper:** `Goalkeeper`
- **Minion_Critter:** `TrophyCritter`
- **Minion_Swarm_Hunter:** `SwarmHunterEnemy`
- **Minion_LastStand:** `LastStandMinion`
- **Minion_FindEnemies2:** `EventModifierBoss`

### 11.6 Окружение: базы, носимое, транспорт

**Базы и сейфы (Pvp_Base):** `Safe`, `RoboWarsBase`, `SafeVoxel`, `SafeDeepsea`, `ArenaTower`, `ArenaBase`, `SafeKatanaKingdom`

**Робот-войны (RoboWars):** `RoboWarsRobo`, `DemonicPetSiege`, `AngelicPetSiege`

**Лутбоксы (LootBox):** `LootBox`, `RoboWarsBox`, `RandomLootBox`

**Мячи и носимое (Carryable):** `LaserBall`, `CaptureFlag`, `HoldingBall`, `VolleyBall`, `BasketBall`, `MultiLaserBall`, `PaintBall`, `VolleyBallZombie`, `AirDisc`, `UNOCard`, `DodgeBall`, `Shuriken`, `Boulder`, `LoveBomb`, `HeistBomb`, `Speeder`, `BoxBomb`, `ChargeBall`, `AirDiscNew`, `NanoIngredient1`, `NanoIngredient2`, `NanoIngredient3`, `NanoIngredient4`, `NanoIngredient5`, `NanoIngredient0`, `NanoIngredient6`, `NanoIngredient7`, `NanoIngredient8`, `NanoIngredient9`, `NanoIngredient10`, `NanoIngredient11`, `NanoIngredient12`, `NanoIngredient13`, `NanoIngredient14`, `NanoIngredient15`, `NanoIngredient16`, `NanoIngredient17`, `NanoIngredient18`, `NanoIngredient19`

**Вагонетки и поезда (Train):** `MineCart0`, `MineCart1`, `MineCart2`, `MineCart3`, `MineCart4`, `Train0`, `Train1`, `Train2`, `Train3`

**Платформы (Payload):** `Payload`, `PayloadSingle`, `MechaVanCart`

**Миньоны арены (ArenaMinion):** `ArenaMelee`, `ArenaRange`, `ArenaSpecialMelee`

**Джунгли (ArenaJungle):** `ArenaBig`, `ArenaSmall`

**Декорации (Decoration):** `ArenaTowerDestroyed`

**Особые версии бойцов (Her0):** `Lightyear`, `LightyearSword`, `LightyearFlight`

### 11.7 Привязка по префиксу имени (в CSV явной ссылки нет — проверяй в игре)

| Объект | Владелец (код / игра) | Тип объекта |
|---|---|---|
| `ArtilleryDudeCover` | `ArtilleryDude` / penny | укрытие |
| `ArtilleryDudeTurret` | `ArtilleryDude` / penny | турель |
| `AssaultShotgunBombBuddy` | `AssaultShotgun` / griff | двойник/напарник |
| `BlackHolePet2` | `BlackHole` / tara | — |
| `BlackHolePetGadget` | `BlackHole` / tara | — |
| `BowDudeTotem` | `BowDude` / bo | тотем |
| `BowDudeTotemBuddy` | `BowDude` / bo | двойник/напарник |
| `CactusCover` | `Cactus` / spike | укрытие |
| `CactusCoverBuddy` | `Cactus` / spike | двойник/напарник |
| `CactusCoverNanoFake` | `Cactus` / spike | — |
| `CocoonerCocoon` | `Cocooner` / charlie | кокон |
| `ControllerAddon` | `Controller` / nani | аддон |
| `CrossBomberVisionTower` | `CrossBomber` / grom | вышка/пушка |
| `DuplicatorPet` | `Duplicator` / lolla | питомец |
| `FleaBigEgg` | `Flea` / eve | яйцо |
| `FleaExtraPet` | `Flea` / eve | питомец |
| `FleaHealingPet` | `Flea` / eve | питомец |
| `FleaOverchargedBigEgg` | `Flea` / eve | яйцо |
| `FleaPet` | `Flea` / eve | питомец |
| `FutureGirlTurret` | `FutureGirl` / wendy | турель |
| `JetpackGirlDamageTower` | `JetpackGirl` / janet | вышка/пушка |
| `KnightPet` | `Knight` / ash | питомец |
| `MagicalGirlFlyArea` | `MagicalGirl` / stella | — |
| `MechaDudeAddon` | `MechaDude` / meg | аддон |
| `MechaDudeReloadTower` | `MechaDude` / meg | вышка/пушка |
| `MechanicTurret` | `Mechanic` / jessie | турель |
| `NinjaFake` | `Ninja` / leon | — |
| `NinjaInvisibleArea` | `Ninja` / leon | — |
| `NinjaInvisibleAreaBuddy` | `Ninja` / leon | двойник/напарник |
| `NinjaMutation` | `Ninja` / leon | — |
| `NinjaNanoPowerClone` | `Ninja` / leon | — |
| `RedirecterCocoon` | `Redirecter` / redirecter | кокон |
| `RedirecterSnakePet` | `Redirecter` / redirecter | питомец |
| `RuffsCover` | `Ruffs` / ruffs | укрытие |
| `SamuraiMeleeEnemy` | `Samurai` / samurai | — |
| `SamuraiRangedEnemy` | `Samurai` / samurai | — |
| `ShamanPet` | `Shaman` / nita | питомец |
| `SpawnerDudeTurret` | `SpawnerDude` / mr.p | турель |
| `SpawnerDudeTurret002` | `SpawnerDude` / mr.p | — |
| `SpawnerDudeTurret003` | `SpawnerDude` / mr.p | — |
| `SuperNovaCactusCover` | `SuperNovaCactus` / — | укрытие |
| `SuperNovaVoodooPet` | `SuperNovaVoodoo` / — | питомец |
| `TrickshotDudeGadgetSkillContainer` | `TrickshotDude` / ricochet | контейнер |
| `TrickshotDudeGadgetSkillContainerBuddy` | `TrickshotDude` / ricochet | двойник/напарник |
| `TwinsPetHyper` | `Twins` / twins | — |
| `VoodooPet` | `Voodoo` / juju | питомец |
