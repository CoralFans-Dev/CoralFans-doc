# 配置文件

## version

+ 配置文件的版本。 `2.0.0` 版CoralFans为 `3`

## locateName

+ 插件语言。支持 `zh_CN` 与 `en_US`

## cfhudRefreshTime

+ cfhud信息显示的刷新时间。单位：Tick

## command

+ 指令配置

### enabled

+ 是否启用该指令

### permission

+ 执行所需权限
+ 可选值如下（从小到大排序）
  + `Any` - 任意玩家
  + `GameDirectors` - 默认的管理员权限
  + `Admin`
  + `Host`
  + `Owner`
  + `Internal`
  
## shortcuts

+ 自定义快捷指令
+ 参见[ShortcutsDoc](/ShortcutsDoc.md)
