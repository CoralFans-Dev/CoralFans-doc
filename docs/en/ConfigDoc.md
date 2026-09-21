# Configuration File

## version

+ Version of the configuration file. For the current version (`26.51.x`), CoralFans uses `7`

## locateName

+ Plugin language. Supports `zh_CN` and `en_US`

## command

+ Command configuration. Each entry contains three fields: `enabled` (whether the command is enabled), `permission` (permission required to execute it), and `command` (command name)
+ Configurable commands include:

| Command | Default Name | Default Permission |
| --- | --- | --- |
| tick | `tick` | GameDirectors |
| func | `func` | GameDirectors |
| self | `self` | Any |
| hsa | `hsa` | Any |
| counter | `counter` | GameDirectors |
| prof | `prof` | Any |
| slime | `slime` | Any |
| village | `village` | Any |
| rotate | `rotate` | Any |
| data | `data` | Any |
| cfhud | `cfhud` | Any |
| log | `log` | Any |
| calculate | `calculate` | Any |
| minerule | `minerule` | GameDirectors |
| freecamera | `freecamera` | Any |
| noclip | `noclip` | Any |
| locate | `cflocate` | Any |

### permission

+ Permission required for execution
+ Available values are as follows (sorted from lowest to highest)
  + `Any` - any player
  + `GameDirectors` - the default operator permission
  + `Admin`
  + `Host`
  + `Owner`
  + `Internal`

## functions

### functions.hud

#### refreshInterval

+ Refresh interval for the cfhud information display. Unit: ticks, default `20`

### functions.hsa

+ Configuration related to HSA visualization
  + `drawInterval` rendering interval (ticks), default `60`
  + `runtimeRemoveScale` removal scale for runtime rendering, default `20`
  + `drawRadius` rendering radius (chunks), default `6`
  + `hsaNorthWestColor` color of the HSA chunk's northwest corner, default `#FFFFFF`
  + `hsaColor` color of the HSA starting point, default `#29ADFF`
  + `structureColor` color of the structure bounding box, default `#10E436`

### functions.locate.duplicatable

+ Configuration related to traceable feature location visualization
  + `drawInterval` rendering interval (ticks), default `60`
  + `runtimeRemoveScale` removal scale for runtime rendering, default `20`
  + `cacheRemoveScale` removal scale for cached data, default `100`
  + `drawRadius` rendering radius (chunks), default `6`
+ Each traceable feature type (netherite, netherSpring, netherFire, glowStone, mushroom, netherGold, netherQuartz, netherMagma, netherGravel, netherBlackstone, netherSoulSand, endIsland, chorusFlower, endGateway) contains the following fields:
  + `enable` whether to enable this type in the `cflocate` command
  + `originPosColor` / `posColor` / `boundColor` rendering colors for the origin/position/bounds (fields vary slightly between types), default `#10E436` / `#FFFFFF`
  + `textColor` text color, default `#FFFFFF`
  + `arrowColor` arrow color, default `#FFFFFF`

### functions.slime

+ Configuration related to slime chunk visualization
  + `drawInterval` rendering interval (ticks), default `60`
  + `runtimeRemoveScale` removal scale for runtime rendering, default `20`
  + `cacheRemoveScale` removal scale for cached data, default `100`
  + `drawRadius` rendering radius (chunks), default `8`
  + `slimeChunkColor` slime chunk color, default `#10E436`

### functions.village

+ Configuration related to village visualization
  + `drawInterval` rendering interval (ticks), default `10`
  + `boundsColor` color of the village bounds, default `#FFFFFF`
  + `raidBoundsColor` color of the raid spawn bounds, default `#10E436`
  + `ironSpawnBoundsColor` color of the iron golem spawn bounds, default `#3003D9`
  + `centerColor` color of the village center, default `#FF0040`
  + `poiBoundsColor` color of the POI query bounds, default `#FFA214`
  + `bedBindColor` color of bed binding, default `#DB3FFD`
  + `ringBindColor` color of bell binding, default `#FFEC27`
  + `workBindColor` color of work block binding, default `#5AC54F`

## shortcut

+ Custom shortcuts
+ See [ShortcutsDoc](/en/ShortcutsDoc.md)
