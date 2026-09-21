# 配置文件

## version

+ 配置文件的版本。当前版本（`26.51.x`）CoralFans为 `7`

## locateName

+ 插件语言。支持 `zh_CN` 与 `en_US`

## command

+ 指令配置。其中每一项均包含 `enabled`（是否启用该指令）、`permission`（执行所需权限）与 `command`（指令名称）三个字段
+ 可配置的指令包括：

| 指令 | 默认名称 | 默认权限 |
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

+ 执行所需权限
+ 可选值如下（从小到大排序）
  + `Any` - 任意玩家
  + `GameDirectors` - 默认的管理员权限
  + `Admin`
  + `Host`
  + `Owner`
  + `Internal`

## functions

### functions.hud

#### refreshInterval

+ cfhud信息显示的刷新时间。单位：Tick，默认 `20`

### functions.hsa

+ HSA可视化相关配置
  + `drawInterval` 绘制间隔（Tick），默认 `60`
  + `runtimeRemoveScale` 运行时绘制的移除倍率，默认 `20`
  + `drawRadius` 绘制半径（区块），默认 `6`
  + `hsaNorthWestColor` HSA区块西北角颜色，默认 `#FFFFFF`
  + `hsaColor` HSA起始点颜色，默认 `#29ADFF`
  + `structureColor` 结构包围盒颜色，默认 `#10E436`

### functions.locate.duplicatable

+ 可回溯地物定位可视化相关配置
  + `drawInterval` 绘制间隔（Tick），默认 `60`
  + `runtimeRemoveScale` 运行时绘制的移除倍率，默认 `20`
  + `cacheRemoveScale` 缓存数据的移除倍率，默认 `100`
  + `drawRadius` 绘制半径（区块），默认 `6`
+ 每一种可回溯地物类型（netherite、netherSpring、netherFire、glowStone、mushroom、netherGold、netherQuartz、netherMagma、netherGravel、netherBlackstone、netherSoulSand、endIsland、chorusFlower、endGateway）均包含以下字段：
  + `enable` 是否在 `cflocate` 指令中启用该类型
  + `originPosColor` / `posColor` / `boundColor` 起始点/位置/边界绘制颜色（不同类型使用的字段略有差异），默认 `#10E436` / `#FFFFFF`
  + `textColor` 文本颜色，默认 `#FFFFFF`
  + `arrowColor` 箭头颜色，默认 `#FFFFFF`

### functions.slime

+ 史莱姆区块可视化相关配置
  + `drawInterval` 绘制间隔（Tick），默认 `60`
  + `runtimeRemoveScale` 运行时绘制的移除倍率，默认 `20`
  + `cacheRemoveScale` 缓存数据的移除倍率，默认 `100`
  + `drawRadius` 绘制半径（区块），默认 `8`
  + `slimeChunkColor` 史莱姆区块颜色，默认 `#10E436`

### functions.village

+ 村庄可视化相关配置
  + `drawInterval` 绘制间隔（Tick），默认 `10`
  + `boundsColor` 村庄范围颜色，默认 `#FFFFFF`
  + `raidBoundsColor` 劫掠刷新边界颜色，默认 `#10E436`
  + `ironSpawnBoundsColor` 铁傀儡刷新范围颜色，默认 `#3003D9`
  + `centerColor` 村庄中心颜色，默认 `#FF0040`
  + `poiBoundsColor` POI查询范围颜色，默认 `#FFA214`
  + `bedBindColor` 床绑定颜色，默认 `#DB3FFD`
  + `ringBindColor` 钟绑定颜色，默认 `#FFEC27`
  + `workBindColor` 工作方块绑定颜色，默认 `#5AC54F`

## shortcut

+ 自定义快捷指令
+ 参见[ShortcutsDoc](/ShortcutsDoc.md)
