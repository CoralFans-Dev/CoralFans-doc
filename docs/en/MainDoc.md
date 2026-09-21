# CoralFans

---

## coralfans

+ About the CoralFans Mod

```text
/coralfans version
```

+ `coralfans version` prints the current version information

## calculate

+ Collects game statistics

```text
/calculate pt
/calculate pt2
```

+ `calculate pt` counts pending tick data within a chunk
+ `calculate pt2` counts pending tick data within a chunk, additionally counting pending ticks that have been removed

## cfhud

+ HUD information display

```text
/cfhud show <isopen: Boolean>
/cfhud <add|remove> <mspt|base|redstone|village|hopper|block|container>
/cfhud removeall
```

+ `cfhud show` configures whether the information is displayed
+ `cfhud add` adds a display item
+ `cfhud remove` removes a display item
+ `cfhud removeall` removes all display items
  + `mspt` - mspt and tps information
  + `base` - basic information, such as current coordinates, chunk, biome, etc.
  + `redstone` - redstone information, equivalent to running `data redstone info`
  + `village` - villager information, equivalent to running `village dweller`
  + `hopper` - hopper counter information, equivalent to running `counter print`
  + `block` - block information, equivalent to running `data block`
  + `container` - container information, equivalent to running `containerreader` (a content preview of the container being pointed at)

## counter

+ Hopper counter

```text
/counter print [channel: int]
/counter reset [channel: int]
```

+ After enabling the hopper counter with `func hoppercounter true`, all hoppers pointing at concrete become infinite hoppers. All items flowing into such a hopper will disappear, but the data is recorded by the plugin, and you can view this data using the `/counter` command. Each of the 16 types of concrete corresponds to one channel (based on its data value).
  + `/counter print [channel: int]` prints the data of the specified channel
  + `/counter reset [channel: int]` clears the data of the specified channel
  + If no channel is specified, the plugin retrieves the data for the channel corresponding to the hopper or concrete being pointed at
+ Note: the hopper counter starts timing from the moment you run `func hoppercounter true`, not at any other time. The data is not saved when the server shuts down.

## data

+ Gets information about blocks, entities, etc.

```text
/data block [blockPos: x y z]
/data block nbt [path: string]
/data block <blockPos: x y z> nbt [path: string]
/data blockentity nbt [path: string]
/data blockentity <blockPos: x y z> nbt [path: string]
/data blockentity highlight [radius: int] [time: int]
/data entity
/data entity nbt [path: string]
/data redstone <signal|info|chunk|conn> [blockPos: x y z]
/data item nbt [path: string]
/data player <player: Player> uuid
```

+ `data block` gets block information (including RuntimeID)
+ `data blockentity` gets block entity information
+ `data entity` gets entity information
+ `data item` gets information about the item in hand
  + `nbt` is used to request NBT information
  + `path` is an optional parameter used to access a specific NBT tag. For example, `a.b[1].c` points to tag c of the second element of array b under tag a under the root tag.
+ `data redstone` gets redstone component information
  + `chunk` marks all redstone components in the current chunk
  + `signal` prints signal-related information
  + `info` prints basic redstone information
  + `conn` marks the specified component (green), child components (yellow), and parent components (red)
+ `data player` gets the UUID of the specified player

## func

+ Provides the ability to adjust global feature configuration

```text
/func forceopen <IsOpen: Boolean>
/func forceplace <all|entity|normal>
/func droppernocost <IsOpen: Boolean>
/func safeexplode <IsOpen: Boolean>
/func autotool <IsOpen: Boolean>
/func autoweapon <IsOpen: Boolean>
/func hoppercounter <IsOpen: Boolean>
/func containerreader <IsOpen: Boolean>
/func autototem <IsOpen: Boolean>
/func autoitem <IsOpen: Boolean>
/func fastdrop <IsOpen: Boolean>
/func nopickup <IsOpen: Boolean>
/func portaldisabled <IsOpen: Boolean>
```

+ `func forceopen` forces containers open
+ `func forceplace` forces block placement
  + `all` ignores all restrictions, `entity` ignores entities, `normal` means normal mode
+ `func droppernocost` droppers do not consume items
+ `func safeexplode` explosions do not destroy terrain
+ `func autotool` automatically switches tools
+ `func autoweapon` automatically switches weapons
+ `func hoppercounter` hopper counter
+ `func containerreader` container preview
+ `func autototem` automatically replenishes totems
+ `func autoitem` automatically restocks items
+ `func fastdrop` quickly throws out all items of the same type in the inventory
+ `func nopickup` disables item pickup
+ `func portaldisabled` disables portals for players

+ func can enable or disable the global switch of certain features. Features are divided into two categories: global features and personal features. For a personal feature to take effect, it must be enabled with both func and self; for a global feature, it only needs to be enabled with the func command, and it will take effect for all players on the server.

## freecamera

+ Free camera

```text
/freecamera
```

+ `freecamera` enables or disables free camera mode. Run it again to disable

## hsa

+ Provides the ability to visualize structure spawn areas (HSA) in-game

```text
/hsa show [IsOpen: Boolean]
/hsa structure show [IsOpen: Boolean]
/hsa list
/hsa structure list
```

+ `hsa show` enables or disables the HSA display. When enabled, the plugin uses particles to draw the starting positions of structure spawn points where HSAs exist in the game (requires a prerequisite Mod and the corresponding resource pack). The default color is black; if HSA points overlap, multiple colors will blend together. If no parameter is specified, it toggles between on/off
+ `hsa structure show` enables or disables the structure bounding box display, which draws the spatial extent of structures. If no parameter is specified, it toggles between on/off
+ `hsa list` lists the coordinates of all HSA starting points in the current chunk
+ `hsa structure list` lists the bounding box ranges of all structures in the current chunk

## locate

+ Locates duplicatable naturally generated features and visualizes them

```text
/cflocate duplicatable <netherite|nether_spring|nether_fire|glow_stone|mushroom|nether_gold|nether_quartz|nether_magma|nether_gravel|blackstone|soul_sand|end_island|chorus_flower|end_gateway> [IsOpen: Boolean]
```

+ `cflocate duplicatable` enables or disables the display of the specified type of duplicatable feature (types not enabled in the config file are unavailable). If `IsOpen` is not specified, it toggles between on/off
  + Duplicatable feature types include: ancient debris (netherite), nether lava spring (nether_spring), nether fire (nether_fire), glowstone (glow_stone), mushroom (mushroom), nether gold ore (nether_gold), nether quartz ore (nether_quartz), magma block (nether_magma), nether gravel (nether_gravel), blackstone (blackstone), soul sand (soul_sand), end island (end_island), chorus flower (chorus_flower), end gateway (end_gateway)

## log

+ Prints some information

```text
/log levelseed
/log pt
/log rpt
```

+ `log levelseed` prints the world seed
+ `log pt` prints the pending tick information of the chunk the player is in
+ `log rpt` prints the random pending tick information of the chunk the player is in

## minerule

+ Used to modify game rules

```text
/minerule fuck_bedrock_no_drop <IsOpen: Boolean>
/minerule fuck_movingBlock_no_drop <IsOpen: Boolean>
/minerule restore_portal_sand_farm <IsOpen: Boolean>
/minerule remove_portal_pigzombie_cd <IsOpen: Boolean>
/minerule restore_ancillary_broken <IsOpen: Boolean>
/minerule fuck_population_cap <IsOpen: Boolean>
/minerule fuck_population_cap global <count: int>
/minerule fuck_population_cap global reset
/minerule fuck_population_cap <dimension: Dimension> <animal|monster|water_animal|villager|ambient|cat|pillager> <surface|underground> <count: float>
/minerule fuck_population_cap <dimension: Dimension> reset
/minerule fuck_piston_reset_velocity <IsOpen: Boolean>
/minerule set_max_pt_consume_per_chunk <maxpt: int>
/minerule mining_72k <IsOpen: Boolean>
```

+ `minerule fuck_bedrock_no_drop` restores the old behavior where bedrock is droppable
+ `minerule fuck_movingBlock_no_drop` fixes the bug where movingBlocks drop nothing when broken
+ `minerule restore_portal_sand_farm` restores the old end-gateway sand farm
+ `minerule remove_portal_pigzombie_cd` removes the 15s portal cooldown of piglins
+ `minerule restore_ancillary_broken` restores the drops of the other half of a two-block-tall block (such as a door) when broken by a piston
+ `minerule fuck_population_cap` removes the population cap limit
  + `fuck_population_cap <IsOpen: Boolean>` enables or disables the population cap modification
  + `fuck_population_cap global <count: int>` sets the global population cap; `reset` restores it to the default value (200)
  + `fuck_population_cap <dimension> <mobtype> <type> <count>` sets the population cap for a specific dimension, a specific mob category, and surface/underground
  + `fuck_population_cap <dimension> reset` resets the population cap of the specified dimension
  + `mobtype` mob categories: animal (animals), monster (monsters), water_animal (water animals), villager (villagers), ambient (ambient mobs), cat (cats), pillager (pillagers)
+ `minerule fuck_piston_reset_velocity` fixes the bug where an entity's velocity is reset when pushed by a piston
+ `minerule set_max_pt_consume_per_chunk` sets the maximum number of pending ticks executed per chunk per gt
+ `minerule mining_72k` fixes the issue where the server-side mining progress is reset during ultra-fast mining (72k mining), preventing continuous block breaking

## noclip

+ Creative mode noclip

```text
/noclip
```

+ `noclip` creative mode noclip

## prof

+ Provides the ability to check server health and locate the source of lag

```text
/prof [normal|entity|chunk|pt|mspt] [numberOfTick: int]
```

+ `prof normal` performs a normal profile, listing the execution times of multiple game entries
+ `prof entity` profiles entity updates
+ `prof chunk` profiles chunk updates (the listed coordinates are chunk coordinates)
+ `prof pt` profiles pending ticks
+ `prof mspt` collects MSPT statistics (max/min/threshold, etc.)
+ `numberOfTick` is an optional parameter specifying how many gt the prof should run for; defaults to 100gt if omitted

## rotate

+ Rotates blocks

```text
/rotate
```

+ `rotate` can rotate the block being pointed at

## self

+ Provides the ability to adjust personal feature configuration

```text
/self autotool <IsOpen: Boolean>
/self autotool mindamage <mindamage: int>
/self autoweapon <IsOpen: Boolean>
/self autoweapon mindamage <mindamage: int>
/self containerreader <IsOpen: Boolean>
/self autototem <IsOpen: Boolean>
/self autoitem <IsOpen: Boolean>
/self fastdrop <IsOpen: Boolean>
/self nopickup <IsOpen: Boolean>
/self portaldisabled <IsOpen: Boolean>
```

+ `self autotool` automatically switches tools
  + `self autotool mindamage` can set the minimum durability of tools. Tools below this durability will not be automatically selected
+ `self autoweapon` automatically switches weapons
  + `self autoweapon mindamage` can set the minimum durability of weapons. Weapons below this durability will not be automatically selected
+ `self containerreader` container preview
+ `self autototem` automatically replenishes totems
+ `self autoitem` automatically restocks items
+ `self fastdrop` quickly throws out all items of the same type in the inventory
+ `self nopickup` disables item pickup
+ `self portaldisabled` disables portals for players
+ When the corresponding feature is not globally enabled with the `func` command, the `self` command will keep setting it to `false`

## slime

+ Provides the ability to visualize slime chunks

```text
/slime check
/slime show [IsOpen: Boolean]
```

+ `slime check` checks whether the current chunk is a slime chunk
+ `slime show` enables or disables slime chunk visualization. If no parameter is specified, it toggles between on/off

## sp

+ Simulated players
+ In CoralFans 2.0.0, we removed the simulated player system and made it a standalone plugin, CFSP
+ See [CFSPCommandDoc](/en/CFSP/CFSPCommandDoc.md)

## tick

+ Provides the ability to change the running speed of the world

```text
/tick query [times: int]
/tick <freeze|reset>
/tick rate <rate: float>
/tick sync [enable: Boolean]
/tick step <step: int>
```

+ `tick query` queries the MSPT
  + The optional parameter `times` specifies how many consecutive gt to query; defaults to a single query if omitted
+ `tick freeze` pauses tick execution
+ `tick reset` resets the game speed to normal
+ `tick rate` sets the game speed; vanilla is 20tps
+ `tick sync` synchronizes the client's game speed with the server (and compensates for flight speed), making client animations match the actual tick rate. If no parameter is specified, it toggles between on/off
+ `tick step` fast-steps forward by the specified number of ticks, and pauses the game after the step finishes

## village

+ Provides the ability to display village information

```text
/village show <bounds|raid|spawn|center|poi|bind> [IsOpen: Boolean]
/village list
/village tickinglist
/village info <id: int>
/village dweller
```

+ `village show <bounds|raid|spawn|center|poi|bind> [IsOpen: Boolean]` toggles village-related visualizations. If `IsOpen` is not specified, it toggles between on/off:
  + `bind` villager binding information visualization
  + `bounds` village bounds visualization
  + `center` village center visualization
  + `poi` POI query range visualization
  + `raid` raid spawn boundary visualization
  + `spawn` iron golem spawn range visualization
+ `village list` lists all currently loaded villages
+ `village tickinglist` lists all currently ticking villages
+ `village info <id: int>` shows the information of the village with the specified VID
+ `village dweller` gets the information of the entity being pointed at (villager)
