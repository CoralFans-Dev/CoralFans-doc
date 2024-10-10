# Shortcuts

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
  + `permission` 自定义短命令的权限，对 `command` type有效。可选值同[config - adminPermission](/ConfigDoc.md#adminpermission)
  + `prevent` 是否拦截原有事件触发
  + `actions` 要执行的指令序列

## 举例

### 打印漏斗计数器信息

```json
{
    "enable": true,
    "type": "useon",
    "item": "cactus",
    "block": "black_concrete",
    "command": "",
    "description": "",
    "permission": "Any",
    "prevent": false,
    "actions": [
        "counter print"
    ]
}
```

+ 上述配置代表：当对准黑色混凝土使用仙人掌时，执行 `counter print` 指令。此快捷方式不阻止原有事件被触发，且是开启的。

### 快捷切换创造

```json
{
    "enable": false,
    "type": "command",
    "item": "",
    "block": "",
    "command": "c",
    "description": "creative",
    "permission": "GameDirectors",
    "prevent": false,
    "actions": [
        "gamemode creative"
    ]
}
```

+ 上述配置代表：当玩家执行 `/c` 命令时，等效于执行 `gamemode creative` 。 `/c` 命令的描述为 `creative` ，需要权限 `GameDirectors` 。此快捷方式是关闭的。
