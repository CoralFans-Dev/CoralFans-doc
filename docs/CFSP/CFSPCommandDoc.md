# CoralFans SimulatedPlayer (CFSP)

> ## Tips
>
> CFSP假人的XUID是固定的，等于 `"-" + std::to_string(std::hash<std::string>()(spname))`
>
> 使用非 `stop` 指令执行的关服操作可能会造成数据丢失。插件不为此负责。

## 指令系统

```text
/sp version
/sp c autorespawn <isopen: bool>
/sp c autojoin <isopen: bool>
/sp list g
/sp list p
/sp g <name: string> create
/sp g <name: string> delete
/sp g <name: string> addsp <simplayer: string>
/sp g <name: string> rmsp <simplayer: string>
/sp g <name: string> addadmin <player: Player>
/sp g <name: string> rmadmin <player: Player>
/sp p <name: string> spawn
/sp p <name: string> spawn pos <pos: x y z>
/sp p <name: string> spawn pos <pos: x y z> rot <rotx: float> <roty: float>
/sp g <name: string> spawn
/sp p <name: string> despawn
/sp g <name: string> despawn
/sp p <name: string> rm
/sp g <name: string> rm
/sp p <name: string> respawn
/sp g <name: string> respawn
/sp p <name: string> stop
/sp g <name: string> stop
/sp p <name: string> sneaking <enable: bool>
/sp g <name: string> sneaking <enable: bool>
/sp p <name: string> swimming <enable: bool>
/sp g <name: string> swimming <enable: bool>
/sp p <name: string> attack [interval: int] [times: int]
/sp g <name: string> attack [interval: int] [times: int]
/sp p <name: string> chat <str: string> [interval: int] [times: int]
/sp g <name: string> chat <str: string> [interval: int] [times: int]
/sp p <name: string> destroy [interval: int] [times: int]
/sp g <name: string> destroy [interval: int] [times: int]
/sp p <name: string> drop
/sp g <name: string> drop
/sp p <name: string> dropinv
/sp g <name: string> dropinv
/sp p <name: string> swap
/sp p <name: string> runcmd <str: string> [interval: int] [times: int]
/sp g <name: string> runcmd <str: string> [interval: int] [times: int]
/sp p <name: string> select <item: Item>
/sp g <name: string> select <item: Item>
/sp p <name: string> interact [interval: int] [times: int]
/sp g <name: string> interact [interval: int] [times: int]
/sp p <name: string> jump [interval: int] [times: int]
/sp g <name: string> jump [interval: int] [times: int]
/sp p <name: string> use [tick: int] [interval: int] [times: int]
/sp g <name: string> use [tick: int] [interval: int] [times: int]
/sp p <name: string> build
/sp g <name: string> build
/sp p <name: string> lookat [pos: x y z]
/sp g <name: string> lookat [pos: x y z]
/sp p <name: string> moveto [pos: x y z]
/sp g <name: string> moveto [pos: x y z]
/sp p <name: string> navto [pos: x y z]
/sp g <name: string> navto [pos: x y z]
/sp p <name: string> script <path: FilePath> [interval: int]
/sp g <name: string> script <path: FilePath> [interval: int] [arg: string]
```

### 基本指令

+ `sp version` 用于打印插件版本信息
+ `sp c` 用于进行假人系统配置。仅假人管理员可执行
  + `sp c autorespawn` 假人死亡自动重生
  + `sp c autojoin` 关服时在线假人在开服时自动加入游戏
+ `sp list` 用于列出相关信息
  + `sp list g` 列出所有组信息
  + `sp list p` 列出所有假人信息

### 操作对象

+ `sp p` 用于操作单一假人。仅假人拥有者或假人管理员可进行操作
+ `sp g` 用于操作假人组。仅组内成员或假人管理员可进行操作
+ `name` 用于指定假人或组的名字

### 独有操作

#### g (group)

+ `create` 创建组
+ `delete` 删除组
+ `addsp <simplayer: string>` 加入假人
+ `rmsp <simplayer: string>` 移出假人
+ `addadmin <player: Player>` 加入成员
+ `rmadmin <player: Player>` 移出成员

#### p (player)

+ `spawn pos <pos: x y z>` 在指定位置创建假人
+ `spawn pos <pos: x y z> rot <rotx: float> <roty: float>` 在指定位置创建假人，并指定其视角
+ `swap` 假人与执行该指令的玩家交换背包、副手、盔甲栏、末影箱

### 共有操作

+ 以下是一些可选参数的默认信息
  + `interval` 默认20，单位tick
  + `times` 默认1，为执行次数，若小于1则为无限执行
  + `tick` 默认40，单位tick
  + `pos` 默认为指向的方块/实体所在的位置

#### 无参操作

+ `spawn` 上线或创建（仅 `p` 操作）假人
+ `despawn` 下线假人
+ `rm` 删除假人
+ `respawn` 假人重生
+ `stop` 假人停止所有动作
+ `drop` 假人丢出手持物品
+ `dropinv` 假人丢出背包物品（不包括副手、盔甲栏、末影箱）
+ `build` 假人开始搭建方块

#### 动作设置操作

+ `sneaking <enable: bool>` 假人潜行
+ `swimming <enable: bool>` 假人游泳/趴下

#### 无参任务操作

+ `attack [interval: int] [times: int]` 假人攻击
+ `destroy [interval: int] [times: int]` 假人破坏
+ `interact [interval: int] [times: int]` 假人交互
+ `jump [interval: int] [times: int]` 假人跳跃

#### 有参任务操作

+ `chat <str: string> [interval: int] [times: int]` 假人发送 `str` 消息
+ `runcmd <str: string> [interval: int] [times: int]` 假人执行 `str` 指令
+ `use [tick: int] [interval: int] [times: int]` 假人使用物品， `tick` 后停止使用

#### 其他操作

+ `select <item: Item>` 假人在背包内搜索指定物品的同类物品并与手持物品切换
+ `lookat [pos: x y z]` 假人看向指定位置
+ `moveto [pos: x y z]` 假人移动到指定位置
+ `navto [pos: x y z]` 假人寻路走到指定位置
+ `script <path: FilePath> [interval: int] [arg: string]` 执行指定脚本。脚本寻找的基路径为 `plugins/CoralFans/data/simplayer/scripts/` 。 `interval` 为脚本 `Tick` 函数的执行间隔， `arg` 为传递给 `Init` 函数的参数
