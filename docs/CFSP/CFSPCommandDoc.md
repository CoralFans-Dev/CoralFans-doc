# CoralFans SimulatedPlayer (CFSP)

> ## Tips
>
> CFSP假人的XUID是固定的，等于 `"-" + std::to_string(std::hash<std::string>()(spname))`
>
> 使用非 `stop` 指令执行的关服操作可能会造成数据丢失。插件不为此负责。

## 指令系统

```text
/sp version
/sp c <autojoin|autorespawn|autodespawn> <isopen: bool>
/sp <addmanager|rmmanager> <player: Player>
/sp
/sp p
/sp g
/sp list p [online|offline]
/sp list g
/sp p create <name: string> [pos: Vec3] [dim: Dimension] [lockUniqueId: bool]
/sp p spawn <name: cfspOfflineSp>
/sp p despawn <name: cfspOnlineSp>
/sp p respawn <name: cfspDeadSp>
/sp p delete <name: cfspSplist> [force: bool]
/sp p info <name: cfspOnlineSp>
/sp p <drop|dropinv|swap|invinfo> <name: cfspOnlineSp>
/sp p select <name: cfspOnlineSp> <item: Item>
/sp p <sneaking|swimming|flying|sprinting> <name: cfspOnlineSp> [enabled: bool]
/sp p <attack|build|interact|jump> <name: cfspOnlineSp> [times: int] [interval: int]
/sp p <use|destroy> <name: cfspOnlineSp> [long: int] [times: int] [interval: int]
/sp p stop <name: cfspOnlineSp>
/sp p <chat|runcmd> <name: cfspOnlineSp> <message: string>
/sp p lookat <name: cfspOnlineSp> [pos: Vec3]
/sp p <moveto|navto> <name: cfspOnlineSp> [pos: Vec3] [speed: float]
/sp p tp <name: cfspOnlineSp> <pos: Vec3> <dim: Dimension>
/sp p perm <name: cfspSplist> <permType: cfspSpPermType> <player: player> <enable: bool>
/sp p permpublic <name: cfspSplist> <permType: cfspSpPermType> <enable: bool>
/sp g create <gname: string>
/sp g <addsp|rmsp> <gname: cfspGroup> <spname: cfspSplist>
/sp g delete <gname: cfspGroup>
/sp g deletesp <gname: cfspGroup> [force: bool]
/sp g <spawn|despawn|respawn> <gname: cfspGroup>
/sp g info <gname: cfspGroup>
/sp g stop <gname: cfspGroup>
/sp g <drop|dropinv|invinfo> <gname: cfspGroup>
/sp g select <gname: cfspGroup> <item: Item>
/sp g <sneaking|swimming|flying|sprinting> <gname: cfspGroup> [enabled: bool]
/sp g <attack|build|interact|jump> <gname: cfspGroup> [times: int] [interval: int]
/sp g <use|destroy> <gname: cfspGroup> [long: int] [times: int] [interval: int]
/sp g <chat|runcmd> <gname: cfspGroup> <message: string>
/sp g lookat <gname: cfspGroup> [pos: Vec3]
/sp g <moveto|navto> <gname: cfspGroup> [pos: Vec3] [speed: float]
/sp g tp <gname: cfspGroup> <pos: Vec3> <dim: Dimension>
/sp g perm <gname: cfspGroup> <permType: cfspGroupPermType> <player: player> <enable: bool>
/sp g permpublic <gname: cfspGroup> <permType: cfspGroupPermType> <enable: bool>
```

### 基本指令

+ `sp version` 用于打印插件版本信息
+ `sp c` 用于进行假人系统配置。仅假人管理员可执行
  + `sp c autojoin` 关服时在线假人在开服时自动加入游戏
  + `sp c autorespawn` 假人死亡自动重生
  + `sp c autordespawn` 假人频繁死亡时自动下线
+ `sp list` 用于列出相关信息
  + `sp list p [online|offline]` 列出所有/在线/离线假人信息
  + `sp list g` 列出所有组信息

### gui指令

+ `sp` 打开gui界面
+ `sp p` 打开假人gui界面
+ `sp g` 打开假人组gui界面

### 假人操作

#### 基础操作

+ `sp p create <name: string> [pos: Vec3] [dim: Dimension] [lockUniqueId: bool]` 创建假人
  + `name` 假人名称
  + `pos` 假人创建坐标,当玩家视线范围内有方块时，默认玩家看向的位置，否则默认玩家当前位置
  + `dim` 假人创建维度，默认玩家当前维度
  + `lockUniqueId` 是否锁定假人uniqueId，如果锁定则假人上下线后不会与三叉戟失去联系，如果不锁定则可以通过上下线假人反复开启试炼宝库
+ `sp p spawn <name: cfspOfflineSp>` 上线假人
+ `sp p despawn <name: cfspOnlineSp>` 下线假人
+ `sp p respawn <name: cfspDeadSp>` 假人重生
+ `sp p delete <name: cfspSplist> [force: bool]` 删除假人
  + `force` 是否强制删除假人。当此参数为true时，可以强制删除背包不为空的假人
+ `sp p info <name: cfspOnlineSp>` 打印假人信息

#### 背包操作

+ `sp p invinfo <name: cfspOnlineSp>` 假人背包信息
+ `sp p drop <name: cfspOnlineSp>` 假人丢弃手持物品
+ `sp p dropinv <name: cfspOnlineSp>` 假人丢弃物品栏内全部物品
+ `sp p swap <name: cfspOnlineSp>` 与假人交换背包（包括装备与末影箱）
+ `sp p select <name: cfspOnlineSp> <item: Item>` 假人在背包中搜索物品并与手持物品切换

#### 状态操作

+ `sp p sneaking <name: cfspOnlineSp> [enabled: bool]` 假人潜行
+ `sp p swimming <name: cfspOnlineSp> [enabled: bool]` 假人游泳
+ `sp p flying <name: cfspOnlineSp> [enabled: bool]` 假人飞行
+ `sp p sprinting <name: cfspOnlineSp> [enabled: bool]` 假人疾跑

#### 假人执行操作

+ 参数含义
  + `times` 动作重复次数
  + `interval` 操作间隔
  + `long` 操作时长

##### 短操作

+ `sp p attack <name: cfspOnlineSp> [times: int] [interval: int]` 假人攻击
+ `sp p build <name: cfspOnlineSp> [times: int] [interval: int]` 假人放置方块
+ `sp p interact <name: cfspOnlineSp> [times: int] [interval: int]` 假人交互
+ `sp p jump <name: cfspOnlineSp> [times: int] [interval: int]` 假人跳跃

##### 短操作

+ `sp p use <name: cfspOnlineSp> [long: int] [times: int] [interval: int]` 假人使用物品
+ `sp p destroy <name: cfspOnlineSp> [long: int] [times: int] [interval: int]` 假人挖掘

#### 看向操作

+ `sp p lookat <name: cfspOnlineSp> [pos: Vec3]` 假人看向操作
  + `pos` 假人看向的坐标，当玩家视线范围内有方块时，默认玩家看向的位置，否则默认玩家当前位置

#### 消息操作

+ `sp p chat <name: cfspOnlineSp> <message: string>` 假人发送消息
+ `sp p runcmd <name: cfspOnlineSp> <message: string>` 假人执行指令
  + `message` 信息内容

#### 移动操作

+ 参数含义
  + `pos` 目标坐标，当玩家视线范围内有方块时，默认玩家看向的位置，否则默认玩家当前位置
  + `speed` 假人移动速度
  + `dim` 目标维度，默认玩家当前位置

+ `sp p moveto <name: cfspOnlineSp> [pos: Vec3] [speed: float]` 假人移动操作
+ `sp p navto <name: cfspOnlineSp> [pos: Vec3] [speed: float]` 假人寻路操作
+ `sp p tp <name: cfspOnlineSp> <pos: Vec3> <dim: Dimension>` 假人传送操作

#### 停止操作

+ `sp p stop <name: cfspOnlineSp>` 假人停止操作

#### 权限管理

+ 参数含义
  + `permType` 权限类别
  + `player` 目标玩家
  + `enable` 是否允许

+ `sp p perm <name: cfspSplist> <permType: cfspSpPermType> <player: player> <enable: bool>` 把假人的某一权限授权给其他玩家
+ `sp p permpublic <name: cfspSplist> <permType: cfspSpPermType> <enable: bool>` 设置假人公共权限

### 假人组操作

#### 基础操作

+ `sp g create <gname: string>` 创建假人组
+ `sp g addsp <gname: cfspGroup> <spname: cfspSplist>` 向假人组中添加假人
+ `sp g rmsp <gname: cfspGroup> <spname: cfspSplist>` 移除假人组中的假人
+ `sp g delete <gname: cfspGroup>` 删除假人组
+ `sp g deletesp <gname: cfspGroup> [force: bool]` 删除组内假人
  + `force` 是否强制删除假人。当此参数为true时，可以强制删除背包不为空的假人

#### 批操作

+ 此部分用于批量控制假人，功能等同于对组内全部假人执行对应假人指令
+ `sp g <spawn|despawn|respawn> <gname: cfspGroup>`
+ `sp g info <gname: cfspGroup>`
+ `sp g stop <gname: cfspGroup>`
+ `sp g <drop|dropinv|invinfo> <gname: cfspGroup>`
+ `sp g select <gname: cfspGroup> <item: Item>`
+ `sp g <sneaking|swimming|flying|sprinting> <gname: cfspGroup> [enabled: bool]`
+ `sp g <attack|build|interact|jump> <gname: cfspGroup> [times: int] [interval: int]`
+ `sp g <use|destroy> <gname: cfspGroup> [long: int] [times: int] [interval: int]`
+ `sp g <chat|runcmd> <gname: cfspGroup> <message: string>`
+ `sp g lookat <gname: cfspGroup> [pos: Vec3]`
+ `sp g <moveto|navto> <gname: cfspGroup> [pos: Vec3] [speed: float]`
+ `sp g tp <gname: cfspGroup> <pos: Vec3> <dim: Dimension>`

#### 权限管理

+ 参数含义
  + `permType` 权限类别
  + `player` 目标玩家
  + `enable` 是否允许

+ `sp g perm <gname: cfspGroup> <permType: cfspGroupPermType> <player: player> <enable: bool>` 把假人组的某一权限授权给其他玩家
+ `sp g permpublic <gname: cfspGroup> <permType: cfspGroupPermType> <enable: bool>` 设置假人组公共权限