# 配置文件

## version

+ 配置文件的版本。 `1.0.0` 版CoralFans为 `2`

## locateName

+ 插件语言。支持 `zh_CN` 与 `en_US`

## cfhudRefreshTime

+ cfhud信息显示的刷新时间。单位：Tick

## simPlayer

+ 假人相关配置

### namePrefix

+ 假人名称前缀

### namePostfix

+ 假人名称后缀

### maxOnline

+ 最大假人同时在线数

### maxOwn

+ 单人最多拥有假人数

### maxGroup

+ 全局最多存在组个数

### maxSpawnCount

+ 最多生成假人次数
+ 为防止内存泄漏，超过此次数后无法生成假人，重启服务器恢复

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

### luaPreload

+ lua预加载脚本内容
+ 该段内容的执行时机为加载库之后、加载内置变量与脚本文件之前
+ 可以用于禁用部分库，以创造安全的执行环境

## command

+ 指令配置

### enabled

+ 是否启用该指令

### permission

+ 执行所需权限。权限可选值同[adminPermission](#adminpermission)

## shortcuts

+ 自定义快捷指令

> `shortcuts` 是一项非常强大的配置功能。仙人掌扳手、仙人掌点击混凝土打印漏斗计数器信息皆依赖此功能。
