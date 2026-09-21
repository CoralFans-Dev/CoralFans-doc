# Shortcuts

> `shortcut` is a very powerful configuration feature. The cactus wrench and clicking concrete with a cactus to print hopper counter info both rely on this feature.

+ Shortcuts are divided into five categories, corresponding to the five arrays in the configuration file:
  + `useons` a player uses an item on a block
  + `uses` a player uses an item
  + `destroys` a player uses an item to destroy any block
  + `commands` custom commands
  + `keyBoards` keyboard keys (client version only)
+ Common fields
  + `enable` whether it is enabled
  + `actions` the sequence of commands to execute. You can use built-in variables in them, which will be replaced at execution time
  + `intercept` whether to intercept the original event trigger
+ `useons` fields
  + `item` the item held by the player
  + `block` the block clicked by the player
+ `uses` fields
  + `item` the item used by the player
+ `destroys` fields
  + `item` the item held by the player while destroying the block
+ `commands` fields
  + `command` the custom short command
  + `description` the description of the custom short command
  + `permission` the permission of the custom short command. Available values are the same as [config - permission](/en/ConfigDoc.md#permission)
+ `keyBoards` fields (client version only)
  + `keyCode` the key value of the key (e.g. `F` `R` `N`)
  + `isDown` whether it triggers on press (`true`) or on release (`false`)
+ Built-in variables
  + `{selfname}` the executor's real name (valid for all types)
  + `{selfx}` the executor's x coordinate (valid for all types)
  + `{selfy}` the executor's y coordinate (valid for all types)
  + `{selfz}` the executor's z coordinate (valid for all types)
  + `{itemname}` the name of the item used (valid for `useons` `uses` `destroys`)
  + `{itemaux}` the auxiliary value of the item used (valid for `useons` `uses` `destroys`)
  + `{blockname}` the name of the targeted block (valid for `useons`)
  + `{blockvariant}` the variant value of the targeted block (valid for `useons`)
  + `{blockx}` the x coordinate of the targeted block (valid for `useons`)
  + `{blocky}` the y coordinate of the targeted block (valid for `useons`)
  + `{blockz}` the z coordinate of the targeted block (valid for `useons`)

## Examples

### Printing Hopper Counter Info

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

+ The above configuration means: when using a cactus on black concrete, the `counter print` command is executed. This shortcut does not intercept the original event trigger, and it is enabled.

### Quickly Switching to Creative

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

+ The above configuration means: when a player executes the `/c` command, it is equivalent to executing `gamemode creative`. The description of the `/c` command is `creative`, and it requires the `GameDirectors` permission. This shortcut is disabled.

### Keyboard Key Trigger (Client Version Only)

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

+ The above configuration means: when the player releases the `F` key, the `freecamera` command is executed to toggle the free camera. This shortcut does not intercept the key event, and it is enabled.
