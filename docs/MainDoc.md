# CoralFans

+ CoralFans文档 建设者[JiaLe1135](https://github.com/JiaLe1135) [odorajbotoj](https://github.com/odorajbotoj)

---

## func

+ 拥有调整全局功能配置的能力

```text
/func autoitem <IsOpen: Boolean>
/func autotool <IsOpen: Boolean>
/func autototem <IsOpen: Boolean>
/func containerreader <IsOpen: Boolean>
/func droppernocost <IsOpen: Boolean>
/func forceopen <IsOpen: Boolean>
/func forceplace <all|entity|normal>
/func huoppercounter <IsOpen: Boolean>
/func maxpt <maxpt: int>
/func noclip <IsOpen: Boolean>
/func safeexplode <IsOpen: Boolean>
```

+ `func autoitem` 自动替换物品
+ `func autotool` 自动切换工具
+ `func autototem` 自动替换图腾
+ `func containerreader` 容器预览
+ `func droppernocost` 投掷器不消耗物品
+ `func forceopen` 强制开启容器
+ `func forceplace` 方块强制放置
  + `all` 表示无视所有限制, `entity` 表示无视实体, `normal`表示正常模式
+ `func huoppercounter` 漏斗计数器
+ `func maxpt` 最大计划刻
+ `func noclip` 创造模式无碰撞箱
+ `func safeexplode` 爆炸不破坏地形

+ `func` 可以开启或者关闭部分功能的全局开关。功能分为两类，全局功能和个人功能。对于个人功能，需要使用 `func` 和 `self` 同时开启该功能才会生效；对于全局功能，只需要使用 `func` 指令开启，该功能则会令全服务器的所有玩家生效。

## self

+ 拥有调整个人功能配置的能力

```text
/self autoitem <IsOpen: Boolean>
/self autotool <IsOpen: Boolean>
/self autotool mindamage <mindamage: int>
/self autototem <IsOpen: Boolean>
/self containerreader <IsOpen: Boolean>
/self noclip <IsOpen: Boolean>
```

+ `func autoitem` 自动替换物品
+ `self autotool` 自动切换工具
  + `self autotool mindamage` 可以设置工具最小耐久值。低于耐久值的工具不会被自动选择
+ `func autototem` 自动替换图腾
+ `self containerreader` 容器预览
+ `self noclip` 创造模式无碰撞箱

## tick

+ 拥有改变世界运行速度的能力

```text
/tick query
/tick <freeze|reset>
/tick rate <rate: float>
/tick step <step: int>
```

+ `tick query` 查询MSPT与TPS
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

## prof

+ 拥有检查服务器健康程度以及定位卡顿源头的能力

```text
/prof [normal|entity|chunk|pt] [numberOfTick: int]
```

+ `prof normal` 进行普通的profile,会列出游戏多个条目的执行时间
+ `prof entity` 对实体更新进行profile
+ `prof chunk` 对区块更新进profile（列出的坐标为区块坐标）
+ `prof pt` 对计划刻进行profile（暂时无法工作）
+ `numberOfTick` 是选填参数，指定prof需要执行的gt数，不填时默认为100gt

## hsa

+ 拥有在游戏内可视化结构生成区域(HSA)的能力

```text
/hsa show <isopen: Boolean>
```

+ `hsa show` 开启或者关闭HSA显示，开启后插件会在游戏内有HSA的地方使用粒子画出结构的刷怪点（需要前置Mod与对应材质包），对于游戏内的四种刷怪点，插件有不同的颜色，具体如下所示：
  + 女巫小屋 红色
  + 地狱堡垒 绿色
  + 海底神殿 黄色
  + 掠夺者前哨站 蓝色

## cfhud

+ 拥有在屏幕上实时显示文字信息的能力

```text
/cfhud <add|remove> <hopper:redstone:village:mspt:base>
/cfhud show <IsOpen: Boolean>
```
+ `cfhud <add|remove>` 添加或删除hud上显示的内容
  + `base` 显示一些基本的信息，包括当前游戏刻度，玩家坐标，视角，指向的方块坐标，和亮度，当前所处位置的群系等等
  + `hopper` 显示指针指向该混泥土所在频道(漏斗计数器)的信息
  + `mspt` 显示服务器最近`1s`的平均mspt和TPS
  + `redstone` 显示红石相关信息
  + `village` 显示指针指向的村民绑定的POI等信息
+ `cfhud show` cfhud功能总开关

## data

+ 拥有显示方块/实体/物品数据的能力

```text
/data block
/data blockentity
/data entity
/data item
/data redstone <chunk|info|signal|conn> [blockPos: x y z]
```

+ `data block [blockPos: x y z] ...` 打印位于 `blockPos` 位置的方块ID,名字等信息,该值缺省时默认为玩家指针指向的方块
+ `data blockentity ...` 打印方块实体的相关信息
+ `data entity ... ` 打印玩家指针指向的实体ID,名字,位置等信息
+ `data item ...` 打印手持物品的相关信息
+ `data redstone <chunk|conn|signal> [blockPos: x y z]` 打印位于 `blockPos` 位置的红石相关信息，该值缺省时默认为玩家指针指向的方块
  + `signal` 展示红石原件的信号强度
  + `info` 展示红石元件的基本性质
  + `chunk` 标记区块的所有红石原件
  + `conn` 标记原件(绿色框)、为该原件的所有信号源(红色框)以及该原件提供能量的所有消费者或者电容器(黄色框)

## counter

+ 拥有查看漏斗接受物品速度的能力

```text
/counter print [channel: int]
/counter reset [channel: int]
```

+ 在使用 `func hoppercounter true` 开启漏斗计数器后，所有对准混凝土的漏斗都将变成无尽的漏斗，所有流向该漏斗的物品都会消失，但是这些数据会被插件记录下来，你可以使用 `/counter` 命令查看这些数据。16种混凝土每一种对应一个频道（根据特殊值）。
  + `/counter print [channel: int]` 打印频道channel的数据
  + `/counter reset [channel: int]` 清除频道channel的数据
  + 不指定频道时，插件会获取指向的漏斗或混凝土对应频道的数据
+ 注意：从使用 `func hoppercounter true` 这一刻开始漏斗计数器就开始计时了，而不是其他时间。

## slime

+ 拥有可视化史莱姆区块的能力

```text
/slime check
/slime show <IsOpen: Boolean>
```

+ `slime check` 检测当前区块是否为史莱姆区块
+ `slime show` 开启或关闭史莱姆区块可视化

## rotate

+ 旋转方块

```text
/rotate
```

+ `rotate` 可以旋转指向的方块

## 配置文件

### version

+ 配置文件的版本。 `0.0.1` 版CoralFans为 `1`

### locateName

+ 插件语言。支持 `zh_CN` 与 `en_US`

### command

+ 指令配置。可以指定指令是否开启与执行所需权限。权限可选值如下
  + `Any`
  + `GameDirectors`
  + `Admin`
  + `Host`
  + `Owner`
  + `Internal`

### shortcuts

+ 自定义快捷指令
  + `enable` 是否开启
  + `type` 快捷指令类型
    + `use` 玩家使用物品
    + `useon` 玩家对着方块使用物品
    + `destroy` 玩家使用物品破坏任意方块
    + `command` 自定义命令
  + `item` 玩家手持物品，对 `use` `useon` `destroy` type有效
  + `blcok` 玩家点击的方块，对 `useon` type有效
  + `command` 自定义的短命令，对 `command` type有效
  + `description` 自定义短命令的描述，对 `command` type有效
  + `permission` 自定义短命令的权限，对 `command` type有效。可选值如下
    + `Any`
    + `GameDirectors`
    + `Admin`
    + `Host`
    + `Owner`
    + `Internal`
  + `prevent` 是否拦截原有事件触发
  + `actions` 要执行的指令序列

> `shortcuts` 是一项非常强大的配置功能。仙人掌扳手、仙人掌点击混凝土打印漏斗信息皆依赖此功能。
