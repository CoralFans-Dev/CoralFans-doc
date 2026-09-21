# CoralFans SimulatedPlayer (CFSP)

> ## Tips
>
> CFSP simulated players have a fixed XUID, equal to `"-" + std::to_string(std::hash<std::string>()(spname))`
>
> Shutting down the server without using the `stop` command may cause data loss. The plugin is not responsible for this.

## Command System

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
/sp p respawn <name: cfspDeadSp>
/sp p delete <name: cfspSplist> [force: bool]
/sp p <despawn|stop|swap|info|invinfo> <name: cfspOnlineSp>
/sp p select <name: cfspOnlineSp> <item: Item>
/sp p <sneaking|swimming|flying|sprinting> <name: cfspOnlineSp> [enabled: bool]
/sp p <attack|build|interact|jump|drop|dropinv> <name: cfspOnlineSp> [times: int] [interval: int]
/sp p <use|destroy> <name: cfspOnlineSp> [long: int] [times: int] [interval: int]
/sp p <chat|runcmd> <name: cfspOnlineSp> <message: string>
/sp p lookat <name: cfspOnlineSp> [pos: Vec3]
/sp p lookat <name: cfspOnlineSp> <facing: north|south|west|east|up|down>
/sp p <moveto|navto> <name: cfspOnlineSp> [pos: Vec3] [speed: float]
/sp p tp <name: cfspOnlineSp> [pos: Vec3] [dim: Dimension]
/sp p perm <name: cfspSplist> <permType: cfspSpPermType> <player: player> <enable: bool>
/sp p permpublic <name: cfspSplist> <permType: cfspSpPermType> <enable: bool>
/sp g create <gname: string>
/sp g <addsp|rmsp> <gname: cfspGroup> <spname: cfspSplist>
/sp g <delete|spawn|despawn|respawn|stop|info|invinfo> <gname: cfspGroup>
/sp g deletesp <gname: cfspGroup> [force: bool]
/sp g <sneaking|swimming|flying|sprinting> <gname: cfspGroup> [enabled: bool]
/sp g <attack|build|interact|jump|drop|dropinv> <gname: cfspGroup> [times: int] [interval: int]
/sp g <use|destroy> <gname: cfspGroup> [long: int] [times: int] [interval: int]
/sp g <chat|runcmd> <gname: cfspGroup> <message: string>
/sp g lookat <gname: cfspGroup> [pos: Vec3]
/sp g lookat <gname: cfspGroup> <facing: north|south|west|east|up|down>
/sp g <moveto|navto> <gname: cfspGroup> [pos: Vec3] [speed: float]
/sp g tp <gname: cfspGroup> [pos: Vec3] [dim: Dimension]
/sp g select <gname: cfspGroup> <item: Item>
/sp g perm <gname: cfspGroup> <permType: cfspGroupPermType> <player: player> <enable: bool>
/sp g permpublic <gname: cfspGroup> <permType: cfspGroupPermType> <enable: bool>
```

### Basic Commands

+ `sp version` prints the plugin version information
+ `sp c` configures the simulated player system. Only SP managers can execute this
  + `sp c autojoin` online simulated players automatically rejoin the game when the server restarts after a server shutdown
  + `sp c autorespawn` simulated players automatically respawn after death
  + `sp c autodespawn` simulated players are automatically despawned when they die frequently
+ `sp list` lists related information
  + `sp list p [online|offline]` lists all/online/offline simulated players
  + `sp list g` lists all SP groups

### GUI Commands

+ `sp` opens the GUI page
+ `sp p` opens the simulated player GUI page
+ `sp g` opens the SP group GUI page

### Simulated Player Operations

#### Basic Operations

+ `sp p create <name: string> [pos: Vec3] [dim: Dimension] [lockUniqueId: bool]` creates a simulated player
  + `name` the simulated player's name
  + `pos` the position where the simulated player is created; defaults to the position the player is looking at if there is a block within their line of sight, otherwise the player's current position
  + `dim` the dimension where the simulated player is created; defaults to the player's current dimension
  + `lockUniqueId` whether to lock the simulated player's uniqueId; if locked, the simulated player will not lose its connection with tridents after despawning and respawning; if not locked, you can repeatedly open trial vaults by despawning and respawning the simulated player
  + When a simulated player is created, its game mode will match that of its creator
+ `sp p spawn <name: cfspOfflineSp>` spawns a simulated player
+ `sp p despawn <name: cfspOnlineSp>` despawns a simulated player
+ `sp p respawn <name: cfspDeadSp>` respawns a simulated player
+ `sp p delete <name: cfspSplist> [force: bool]` deletes a simulated player
  + `force` whether to forcibly delete the simulated player. When this parameter is true, a simulated player whose inventory is not empty can be forcibly deleted
+ `sp p info <name: cfspOnlineSp>` prints the simulated player's information

#### Inventory Operations

+ `sp p invinfo <name: cfspOnlineSp>` shows the simulated player's inventory information
+ `sp p drop <name: cfspOnlineSp> [times: int] [interval: int]` makes the simulated player drop its selected item
+ `sp p dropinv <name: cfspOnlineSp> [times: int] [interval: int]` makes the simulated player drop all items in its inventory
+ `sp p swap <name: cfspOnlineSp>` swaps inventories with the simulated player (including equipment and ender chest)
+ `sp p select <name: cfspOnlineSp> <item: Item>` makes the simulated player search its inventory for the item and switch it with the selected item

#### State Operations

+ `sp p sneaking <name: cfspOnlineSp> [enabled: bool]` makes the simulated player sneak
+ `sp p swimming <name: cfspOnlineSp> [enabled: bool]` makes the simulated player swim
+ `sp p flying <name: cfspOnlineSp> [enabled: bool]` makes the simulated player fly
+ `sp p sprinting <name: cfspOnlineSp> [enabled: bool]` makes the simulated player sprint

#### Simulated Player Actions

+ Parameter meanings
  + `times` number of times to repeat the action
  + `interval` interval between actions
  + `long` duration of the action

##### Short Actions

+ `sp p attack <name: cfspOnlineSp> [times: int] [interval: int]` makes the simulated player attack
+ `sp p build <name: cfspOnlineSp> [times: int] [interval: int]` makes the simulated player place blocks
+ `sp p interact <name: cfspOnlineSp> [times: int] [interval: int]` makes the simulated player interact
+ `sp p jump <name: cfspOnlineSp> [times: int] [interval: int]` makes the simulated player jump

##### Long Actions

+ `sp p use <name: cfspOnlineSp> [long: int] [times: int] [interval: int]` makes the simulated player use an item
+ `sp p destroy <name: cfspOnlineSp> [long: int] [times: int] [interval: int]` makes the simulated player mine

#### Look At Operations

+ `sp p lookat <name: cfspOnlineSp> [pos: Vec3]` makes the simulated player look at a position
  + `pos` the position the simulated player looks at; defaults to the position the player is looking at if there is a block within their line of sight, otherwise the player's current position
+ `sp p lookat <name: cfspOnlineSp> <facing: north|south|west|east|up|down>` makes the simulated player look in a specified direction

#### Message Operations

+ `sp p chat <name: cfspOnlineSp> <message: string>` makes the simulated player send a message
+ `sp p runcmd <name: cfspOnlineSp> <message: string>` makes the simulated player execute a command
  + `message` the message content

#### Movement Operations

+ Parameter meanings
  + `pos` the target position; defaults to the position the player is looking at if there is a block within their line of sight, otherwise the player's current position
  + `speed` the simulated player's movement speed
  + `dim` the target dimension; defaults to the player's current position

+ `sp p moveto <name: cfspOnlineSp> [pos: Vec3] [speed: float]` makes the simulated player move
+ `sp p navto <name: cfspOnlineSp> [pos: Vec3] [speed: float]` makes the simulated player navigate
+ `sp p tp <name: cfspOnlineSp> [pos: Vec3] [dim: Dimension]` teleports the simulated player

#### Stop Operation

+ `sp p stop <name: cfspOnlineSp>` stops the simulated player's actions

#### Permission Management

+ Parameter meanings
  + `permType` the permission type; available values: `all` (all permissions), `Spawn`, `Despawn`, `Respawn`, `Delete`, `Stop`, `Drop`, `DropInv`, `Swap`, `Sneaking`, `Swimming`, `Flying`, `Sprinting`, `Attack`, `Build`, `Interact`, `Jump`, `Use`, `Destroy`, `Chat`, `RunCmd`, `Select`, `LookAt`, `MoveTo`, `NavTo`, `Tp`, `BeAddedToGroup` (allow being added to SP groups)
  + `player` the target player
  + `enable` whether to allow

+ `sp p perm <name: cfspSplist> <permType: cfspSpPermType> <player: player> <enable: bool>` grants a specific permission of the simulated player to another player
+ `sp p permpublic <name: cfspSplist> <permType: cfspSpPermType> <enable: bool>` sets the simulated player's public permission

### SP Group Operations

#### Basic Operations

+ `sp g create <gname: string>` creates an SP group
+ `sp g addsp <gname: cfspGroup> <spname: cfspSplist>` adds a simulated player to an SP group
+ `sp g rmsp <gname: cfspGroup> <spname: cfspSplist>` removes a simulated player from an SP group
+ `sp g delete <gname: cfspGroup>` deletes an SP group
+ `sp g deletesp <gname: cfspGroup> [force: bool]` deletes the simulated players in the group
  + `force` whether to forcibly delete the simulated players. When this parameter is true, simulated players whose inventories are not empty can be forcibly deleted

#### Batch Operations

+ This section is used to control simulated players in batch; the functionality is equivalent to executing the corresponding simulated player command on every simulated player in the group
+ `sp g <spawn|despawn|respawn> <gname: cfspGroup>`
+ `sp g info <gname: cfspGroup>`
+ `sp g stop <gname: cfspGroup>`
+ `sp g <drop|dropinv|invinfo> <gname: cfspGroup>` (`drop` and `dropinv` support the `[times: int] [interval: int]` parameters)
+ `sp g select <gname: cfspGroup> <item: Item>`
+ `sp g <sneaking|swimming|flying|sprinting> <gname: cfspGroup> [enabled: bool]`
+ `sp g <attack|build|interact|jump> <gname: cfspGroup> [times: int] [interval: int]`
+ `sp g <use|destroy> <gname: cfspGroup> [long: int] [times: int] [interval: int]`
+ `sp g <chat|runcmd> <gname: cfspGroup> <message: string>`
+ `sp g lookat <gname: cfspGroup> [pos: Vec3]`
+ `sp g lookat <gname: cfspGroup> <facing: north|south|west|east|up|down>`
+ `sp g <moveto|navto> <gname: cfspGroup> [pos: Vec3] [speed: float]`
+ `sp g tp <gname: cfspGroup> [pos: Vec3] [dim: Dimension]`

#### Permission Management

+ Parameter meanings
  + `permType` the permission type; available values: `all` (all permissions), `AddSp`, `RmSp`, `Delete`, `Spawn`, `Despawn`, `Respawn`, `DeleteSp`, `Stop`, `Drop`, `DropInv`, `Sneaking`, `Swimming`, `Flying`, `Sprinting`, `Attack`, `Build`, `Interact`, `Jump`, `Use`, `Destroy`, `Chat`, `RunCmd`, `LookAt`, `MoveTo`, `NavTo`, `Tp`, `Select`
  + `player` the target player
  + `enable` whether to allow

+ `sp g perm <gname: cfspGroup> <permType: cfspGroupPermType> <player: player> <enable: bool>` grants a specific permission of the SP group to another player
+ `sp g permpublic <gname: cfspGroup> <permType: cfspGroupPermType> <enable: bool>` sets the SP group's public permission
