# CFSP Configuration File

## Config.json

### version

+ The version of the Config.json configuration file. For the current version (`26.51.x`) of CFSP it is `3`

### enabled

+ Whether to enable the simulated player system

### permission

+ Base permission level for simulated player commands

### namePrefix

+ Simulated player name prefix

### namePostfix

+ Simulated player name suffix

### autoRespawn 

+ Simulated players automatically respawn after death

### autojoin

+ Simulated players online at server shutdown automatically join the game when the server starts

### autoDespawn

+ Simulated players automatically go offline when they die frequently

### maxOnline

+ Maximum number of simulated players online at the same time

### maxOwn

+ Maximum number of simulated players a single player can own

### maxOnlinePerPlayer

+ Maximum number of simulated players a single player can have online at the same time

### maxGroup

+ Maximum number of groups a single player can own

### autoDespawnCount & autoDespawninterval

+ When autoDespawn is enabled, if a simulated player dies autoDespawnCount times within autoDespawninterval gt, the simulated player goes offline

### adminPermission

+ Permission required for simulated player managers
+ Available values are as follows (sorted from lowest to highest)
  + `Any` - any player
  + `GameDirectors` - the default manager permission
  + `Admin`
  + `Host`
  + `Owner`
  + `Internal`

### listType

+ The list type, applied to the list below
+ Available values are as follows
  + `disabled` - disable this feature
  + `blacklist` - the list is a blacklist
  + `whitelist` - the list is a whitelist

### list

+ The list
+ A string array; values should be player UUIDs

### superManagerList

+ The manager list

### luaPreload

+ Content of the lua preload script
+ This content is executed after the libraries are loaded and before the built-in variables and script files are loaded
+ Can be used to disable certain libraries to create a safe execution environment

## PermissionConfig.json

### version

+ The version of the PermissionConfig.json configuration file. For the current version of CFSP it is `1`

### Feature entries

+ Each feature entry corresponds to one simulated player operation (such as `spCreate`, `spSpawn`, `spLookAt`, `groupCreate`, etc.), and contains the following fields:

#### enabled

+ Whether to enable this command/operation

#### permission

+ The permission required to execute it. Available values are the same as [adminpermission](#adminpermission)
