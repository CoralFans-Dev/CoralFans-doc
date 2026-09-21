# Shortcuts

> `shortcut` 是一项非常强大的配置功能。仙人掌扳手、仙人掌点击混凝土打印漏斗计数器信息皆依赖此功能。

+ 快捷指令分为五类，分别对应配置文件中的五个数组：
  + `useons` 玩家对着方块使用物品
  + `uses` 玩家使用物品
  + `destroys` 玩家使用物品破坏任意方块
  + `commands` 自定义命令
  + `keyBoards` 键盘按键（仅客户端版可用）
+ 通用字段
  + `enable` 是否开启
  + `actions` 要执行的指令序列。您可以在其中使用一些内建变量，他们会在执行时被替换
  + `intercept` 是否拦截原有事件触发
+ `useons` 字段
  + `item` 玩家手持物品
  + `block` 玩家点击的方块
+ `uses` 字段
  + `item` 玩家使用的物品
+ `destroys` 字段
  + `item` 玩家破坏方块时手持的物品
+ `commands` 字段
  + `command` 自定义的短命令
  + `description` 自定义短命令的描述
  + `permission` 自定义短命令的权限。可选值同[config - permission](/ConfigDoc.md#permission)
+ `keyBoards` 字段（仅客户端版可用）
  + `keyCode` 按键的键值（如 `F` `R` `N`）
  + `isDown` 是按下触发（`true`）还是松开触发（`false`）
+ 内建变量
  + `{selfname}` 执行者真名（所有类型有效）
  + `{selfx}` 执行者x坐标（所有类型有效）
  + `{selfy}` 执行者y坐标（所有类型有效）
  + `{selfz}` 执行者z坐标（所有类型有效）
  + `{itemname}` 使用的物品的名称（对 `useons` `uses` `destroys` 有效）
  + `{itemaux}` 使用的物品的特殊值（对 `useons` `uses` `destroys` 有效）
  + `{blockname}` 对准方块的名称（对 `useons` 有效）
  + `{blockvariant}` 对准方块的特殊值（对 `useons` 有效）
  + `{blockx}` 对准方块的x坐标（对 `useons` 有效）
  + `{blocky}` 对准方块的y坐标（对 `useons` 有效）
  + `{blockz}` 对准方块的z坐标（对 `useons` 有效）

## 举例

### 打印漏斗计数器信息

```json
"useons": [
    {
        "enable": true,
        "item": "cactus",
        "block": "black_concrete",
        "intercept": false,
        "actions": [
            "counter print"
        ]
    }
]
```

+ 上述配置代表：当对准黑色混凝土使用仙人掌时，执行 `counter print` 指令。此快捷方式不拦截原有事件被触发，且是开启的。

### 快捷切换创造

```json
"commands": [
    {
        "enable": false,
        "command": "c",
        "description": "creative",
        "permission": "GameDirectors",
        "actions": [
            "gamemode creative"
        ]
    }
]
```

+ 上述配置代表：当玩家执行 `/c` 命令时，等效于执行 `gamemode creative` 。 `/c` 命令的描述为 `creative` ，需要权限 `GameDirectors` 。此快捷方式是关闭的。

### 键盘按键触发（仅客户端版可用）

```json
"keyBoards": [
    {
        "enable": true,
        "keyCode": "F",
        "isDown": false,
        "intercept": false,
        "actions": [
            "freecamera"
        ]
    }
]
```

+ 上述配置代表：当玩家松开 `F` 键时，执行 `freecamera` 指令以切换自由视角。此快捷方式不拦截按键事件，且是开启的。
