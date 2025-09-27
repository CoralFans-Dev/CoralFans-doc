# CFSP配置文件

## Config.json

### version

+ Config.json配置文件的版本。 `3.0.0` 版CFSP为 `3`

### permission

+ 假人指令基础权限等级

### namePrefix

+ 假人名称前缀

### namePostfix

+ 假人名称后缀

### autoRespawn 

+ 假人死亡自动重生

### autojoin

+ 关服时在线假人在开服时自动加入游戏

### autoDespawn

+ 假人频繁死亡时自动下线

### maxOnline

+ 最大假人同时在线数

### maxOwn

+ 单人最多拥有假人数

### maxGroup

+ 单人最多拥有组个数

### autoDespawnCount & autoDespawninterval

+ 开启autoDespawn时，当autoDespawninterval gt内死亡autoDespawnCount次，假人下线

### adminPermission

+ 假人管理员所需权限
+ 可选值如下（从小到大排序）
  + `Any` - 任意玩家
  + `GameDirectors` - 默认的管理员权限
  + `Admin`
  + `Host`
  + `Owner`
  + `Internal`

### listType

+ 名单类型，针对下文的list
+ 可选值如下
  + `disabled` - 禁用此功能
  + `blacklist` - 名单为黑名单
  + `whitelist` - 名单为白名单

### list

+ 名单
+ 字符串数组，值应为玩家UUID

### superManagerList

+ 管理员名单

### luaPreload

+ lua预加载脚本内容
+ 该段内容的执行时机为加载库之后、加载内置变量与脚本文件之前
+ 可以用于禁用部分库，以创造安全的执行环境

## PermissionConfig.h

### version

+ PermissionConfig.json配置文件的版本。 `3.0.0` 版CFSP为 `1`

### func 

#### enabled

+ 是否启用该指令

#### permission

+ 执行所需权限，可选值同[adminpermission](#adminpermission)
