# CoralFans

---

## coralfans

+ 关于 CoralFans Mod

```text
/coralfans version
```

+ `coralfans version` 打印当前版本信息

## calculate

+ 统计游戏数据

```text
/calculate pt
```

+ `calculate pt` 统计区块内计划刻数据

## cfhud

+ HUD信息显示

```text
/cfhud show <isopen: Boolean>
/cfhud <add|remove> <mspt|base|redstone|village|hopper|block>
```

+ `cfhud show` 配置是否显示信息
+ `cfhud add` 增加一条显示项
+ `cfhud remove` 删除一条显示项
  + `mspt` - mspt与tps信息
  + `base` - 基本信息，如当前坐标、区块等
  + `redstone` - 红石信息，等同于执行 `data redstone info`
  + `village` - 村民信息，等同于执行 `village dweller`
  + `hopper` - 漏斗计数器信息，等同于执行 `counter print`
  + `block` - 方块信息，等同于执行 `data block`

## counter

+ 漏斗计数器

```text
/counter print [channel: int]
/counter reset [channel: int]
```

+ 在使用 `func hoppercounter true` 开启漏斗计数器后，所有对准混凝土的漏斗都将变成无尽的漏斗，所有流向该漏斗的物品都会消失，但是这些数据会被插件记录下来，你可以使用 `/counter` 命令查看这些数据。16种混凝土每一种对应一个频道（根据特殊值）。
  + `/counter print [channel: int]` 打印频道channel的数据
  + `/counter reset [channel: int]` 清除频道channel的数据
  + 不指定频道时，插件会获取指向的漏斗或混凝土对应频道的数据
+ 注意：从使用 `func hoppercounter true` 这一刻开始漏斗计数器就开始计时了，而不是其他时间。数据在服务器关闭时不会保存。

## data

+ 获取方块或实体等的信息

```text
/data block [blockPos: x y z]
/data block nbt [path: string]
/data block <blockPos: x y z> nbt [path: string]
/data blockentity nbt [path: string]
/data blockentity <blockPos: x y z> nbt [path: string]
/data blockentity highlight [radius: int] [time: int]
/data entity
/data entity nbt [path: string]
/data redstone <signal|info|chunk|conn> [blockPos: x y z]
/data item nbt [path: string]
/data player <player: Player> uuid
```

+ `data block` 获取方块信息
+ `data blockentity` 获取方块实体信息
+ `data entity` 获取实体信息
+ `data item` 获取手持物品信息
  + `nbt` 用于指定获取nbt信息
  + `path` 是可选参数，用于访问特定的Nbt Tag。如 `a.b[1].c` 指向根标签下a标签下b数组的第二个元素的c标签。
+ `data redstone` 获取红石原件信息
  + `chunk` 标记所在区块的所有红石原件
  + `signal` 打印信号相关信息
  + `info` 打印红石基本信息
  + `conn` 标记指定原件（绿色）、子原件（黄色）、父原件（红色）
+ `data player` 获取指定玩家的UUID

## func

+ 拥有调整全局功能配置的能力

```text
/func forceopen <IsOpen: Boolean>
/func forceplace <all|entity|normal>
/func noclip <IsOpen: Boolean>
/func droppernocost <IsOpen: Boolean>
/func safeexplode <IsOpen: Boolean>
/func autotool <IsOpen: Boolean>
/func hoppercounter <IsOpen: Boolean>
/func maxpt <maxpt: int>
/func containerreader <IsOpen: Boolean>
/func autototem <IsOpen: Boolean>
/func autoitem <IsOpen: Boolean>
/func fastdrop <IsOpen: Boolean>
/func portaldisabled <IsOpen: Boolean>
```

+ `func forceopen` 强制开启容器
+ `func forceplace` 方块强制放置
  + `all` 表示无视所有限制, `entity` 表示无视实体, `normal`表示正常模式
+ `func noclip` 创造模式无碰撞箱
+ `func droppernocost` 投掷器不消耗物品
+ `func safeexplode` 爆炸不破坏地形
+ `func autotool` 自动切换工具
+ `func hoppercounter` 漏斗计数器
+ `func maxpt` 最大计划刻
+ `func containerreader` 容器预览
+ `func autototem` 自动补充图腾
+ `func autoitem` 物品自动补货
+ `func fastdrop` 快速扔出背包所有同类物品
+ `func portaldisabled` 玩家禁用传送门

+ func可以开启或者关闭部分功能的全局开关。功能分为两类，全局功能和个人功能。对于个人功能，需要使用func和self同时开启该功能才会生效；对于全局功能，只需要使用func指令开启，该功能则会令全服务器的所有玩家生效。

## hsa

+ 拥有在游戏内可视化结构生成区域(HSA)的能力

```text
/hsa show <isopen: Boolean>
```

+ `hsa show` 开启或者关闭HSA显示，开启后插件会在游戏内有HSA的地方使用粒子画出结构的刷怪点起始位置（需要前置Mod与对应材质包），默认黑色，如若hsa点位重合，则会出现多种色彩叠加的情况

## log

+ 打印一些信息

```text
/log levelseed
/log pt
/log rpt
```

+ `log levelseed` 打印存档种子
+ `log pt` 打印玩家所在区块的计划刻信息
+ `log rpt` 打印玩家所在区块的随机计划刻信息

## minerule

+ 用于修改游戏规则

```text
/minerule fuck_bedrock_no_drop <IsOpen: Boolean>
/minerule fuck_movingBlock_no_drop <IsOpen: Boolean>
/minerule remove_portal_pigzombie_cd <IsOpen: Boolean>
/minerule replicated_portal_sand_farm <IsOpen: Boolean>
```

+ `minerule fuck_bedrock_no_drop` 还原旧版本基岩可掉落
+ `minerule fuck_movingBlock_no_drop` 修复movingBlock破坏时不掉落的bug
+ `minerule remove_portal_pigzombie_cd` 移除猪人15s传送cd
+ `minerule replicated_portal_sand_farm` 还原旧版本折跃门刷沙机

## noclip

+ 创造模式无碰撞箱

```text
/noclip
```

+ `noclip` 创造模式无碰撞箱

## prof

+ 拥有检查服务器健康程度以及定位卡顿源头的能力

```text
/prof [normal|entity|chunk|pt] [numberOfTick: int]
```

+ `prof normal` 进行普通的profile,会列出游戏多个条目的执行时间
+ `prof entity` 对实体更新进行profile
+ `prof chunk` 对区块更新进profile（列出的坐标为区块坐标）
+ `prof pt` 对计划刻进行profile
+ `numberOfTick` 是选填参数，指定prof需要执行的gt数，不填时默认为100gt

## rotate

+ 旋转方块

```text
/rotate
```

+ `rotate` 可以旋转指向的方块

## self

+ 拥有调整个人功能配置的能力

```text
/self autotool <IsOpen: Boolean>
/self autotool mindamage <mindamage: int>
/self containerreader <IsOpen: Boolean>
/self autototem <IsOpen: Boolean>
/self autoitem <IsOpen: Boolean>
/self fastdrop <IsOpen: Boolean>
/self portaldisabled <IsOpen: Boolean>
```

+ `self autotool` 自动切换工具
  + `self autotool mindamage` 可以设置工具最小耐久值。低于耐久值的工具不会被自动选择
+ `self containerreader` 容器预览
+ `self autototem` 自动补充图腾
+ `self autoitem` 物品自动补货
+ `self fastdrop` 快速扔出背包所有同类物品
+ `self portaldisabled` 玩家禁用传送门
+ 当对应的功能没有在 `func` 指令中全局开启时， `self` 指令会一直将其配置为 `false`

## slime

+ 拥有可视化史莱姆区块的能力

```text
/slime check
/slime show <IsOpen: Boolean>
```

+ `slime check` 检测当前区块是否为史莱姆区块
+ `slime show` 开启或关闭史莱姆区块可视化

## sp

+ 假人
+ 在CoralFans 2.0.0版本中，我们移除了假人系统，并将其做成了独立插件CFSP
+ 参见[CFSPCommandDoc](/CFSP/CFSPCommandDoc.md)

## tick

+ 拥有改变世界运行速度的能力

```text
/tick query
/tick <freeze|reset>
/tick rate <rate: float>
/tick step <step: int>
```

+ `tick query` 查询MSPT
+ `tick freeze` 暂停tick执行
+ `tick reset` 重置游戏速率至正常
+ `tick rate` 设置游戏速率，原版为20tps
+ `tick step` 加速步进，并在步进结束后暂停游戏运行
  + 该命令后可接 `t` `s` `d` 单位，分别代表步进tick，秒，游戏日。如步进一游戏日为 `tick step 1d`

## village

+ 拥有显示村庄信息的能力

```text
/village show <bounds|raid|spawn|center|poi|bind> <IsOpen: Boolean>
/village list
/village info <id: softenum>
/village dweller
```

+ `village show <bounds|raid|spawn|center|poi|bind> <IsOpen: Boolean>` 用于开关村庄相关的可视化：
  + `bind` 村民绑定信息可视化
  + `bounds` 村庄范围可视化
  + `center` 村庄中心可视化
  + `poi` POI的查询范围可视化
  + `raid` 劫掠刷新边界可视化
  + `spawn` 铁傀儡刷新范围可视化
+ `village list` 列出所有正在加载的村庄
+ `village info <id: softenum>` 显示指定VID或UUID的村庄的信息
+ `village dweller` 获取指向实体（村民）的信息
