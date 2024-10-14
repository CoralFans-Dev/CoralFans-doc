# CFSP Lua Api Doc

## 脚本系统

> 脚本系统使用 `Lua 5.4.7` 。
>
> 脚本系统非常强大，但是，您只应该执行信任的脚本。否则这可能会对您的系统造成破坏。插件不对此负责。
>
> 本章内容不建议普通用户/初学者阅读。您需要拥有Lua基础才能理解本章内容。

### 基本介绍

脚本存放于 `plugins/CoralFans/data/simplayer/scripts/` 下。其内部至少应有两个函数： `Init` 和 `Tick` 。两个函数均返回 `boolean` 类型的值。若返回值为 `false` 则中断脚本执行。特别地， `Init` 函数接受一个 `string` 类型的参数，这使得玩家可以通过指令向脚本传参。

以下是一个最简单的可执行脚本。该脚本会执行一次 `Init` 函数与一次 `Tick` 函数。第一次执行 `Tick` 函数时就返回了 `false` ，故不会重复执行。

```lua
function Init(arg)
    return true
end
function Tick()
    return false
end
```

### 执行流程

1. 新建Lua虚拟机并打开标准库
2. 加载 `log` 函数
3. 执行配置文件中的 `preload` 字符串 ( `luaL_dostring` )
4. 加载内建类型与变量
5. 将脚本的执行文件夹添加到 `require` 的寻找路径中
6. 执行脚本 ( `luaL_dofile` )
7. 运行一次 `Init` 函数 ( `lua_pcall` )
8. 如果 `Init` 函数返回 `true` ，则第一次执行 `Tick` 函数 ( `lua_pcall` )
9. 如果第一次执行 `Tick` 函数返回 `true` ，则将 `Tick` 函数的执行交由调度器管理，继续执行。
10. 若执行过程中出错/函数返回 `false` ，则中断执行。

+ 你可以在[src/cfsp/simplayer/luaapi/SpLuaApi.cpp#L49](https://github.com/CoralFans-Dev/CFSP/blob/develop/src/cfsp/simplayer/luaapi/SpLuaApi.cpp#L49)中找到更多信息

### 内建数据

#### 函数

##### log

```lua
log(...)
```

+ 输出传入的信息，以 `\t` 分隔。该函数会调用传入参数的 `__tostring` 元方法。
+ 建议在脚本中使用 `log` 替换 `print` 。

#### 类型

+ 所有的类型均由 `userdata` 实现

##### vec3

+ 浮点坐标

###### 对于类型 ( `foo.bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `new` | `number`, `number`, `number` | `vec3` | 构造一个 `vec3` |
| `newHalf` | - | `vec3` | 构造C++中的 `Vec3::HALF` |
| `newMax` | - | `vec3` | 构造C++中的 `Vec3::MAX` |
| `newMin` | - | `vec3` | 构造C++中的 `Vec3::MIN` |
| `newNegUnitX` | - | `vec3` | 构造C++中的 `Vec3::NEG_UNIT_X` |
| `newNegUnitY` | - | `vec3` | 构造C++中的 `Vec3::NEG_UNIT_Y` |
| `newNegUnitZ` | - | `vec3` | 构造C++中的 `Vec3::NEG_UNIT_Z` |
| `newOne` | - | `vec3` | 构造C++中的 `Vec3::ONE` |
| `newTwo` | - | `vec3` | 构造C++中的 `Vec3::TWO` |
| `newUnitX` | - | `vec3` | 构造C++中的 `Vec3::UNIT_X` |
| `newUnitY` | - | `vec3` | 构造C++中的 `Vec3::UNIT_Y` |
| `newUnitZ` | - | `vec3` | 构造C++中的 `Vec3::UNIT_Z` |
| `newZero` | - | `vec3` | 构造C++中的 `Vec3::ZERO` |

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `get` | - | `number`, `number`, `number` | 获取存储的xyz值 |

###### 元方法

| 函数 | 用途 |
| --- | --- |
| `__tostring` | 调用C++中的 `Vec3::toString` |
| `__add` | 调用C++中的 `Vec3::operator+` |
| `__sub` | 调用C++中的 `Vec3::operator-` |
| `__eq` | 调用C++中的 `Vec3::operator==` |

##### blockpos

+ 整数坐标/方块坐标

###### 对于类型 ( `foo.bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `new` | `integer`, `integer`, `integer` | `blockpos` | 构造一个 `blockpos` |
| `newMax` | - | `blockpos` | 构造C++中的 `BlockPos::MAX` |
| `newMin` | - | `blockpos` | 构造C++中的 `BlockPos::MIN` |
| `newOne` | - | `blockpos` | 构造C++中的 `BlockPos::ONE` |
| `newZero` | - | `blockpos` | 构造C++中的 `BlockPos::ZERO` |

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `get` | - | `integer`, `integer`, `integer` | 获取存储的xyz值 |
| `bottomCenter` | - | `vec3` | 调用C++中的 `BlockPos::bottomCenter` |
| `center` | - | `vec3` | 调用C++中的 `BlockPos::center` |
| `toVec3` | - | `vec3` | 调用C++中的 `BlockPos::operator class Vec3` |
| `neighbor` | - | `blockpos` | 调用C++中的 `BlockPos::neighbor` |

###### 元方法

| 函数 | 用途 |
| --- | --- |
| `__tostring` | 调用C++中的 `BlockPos::toString` |
| `__add` | 调用C++中的 `BlockPos::operator+` |
| `__sub` | 调用C++中的 `BlockPos::operator-` |
| `__eq` | 调用C++中的 `BlockPos::operator==` |

##### vec2

+ 浮点视角

###### 对于类型 ( `foo.bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `new` | `number`, `number` | `vec2` | 构造一个 `vec2` |
| `newLowest` | - | `vec2` | 构造C++中的 `Vec2::LOWEST` |
| `newMax` | - | `vec2` | 构造C++中的 `Vec2::MAX` |
| `newMin` | - | `vec2` | 构造C++中的 `Vec2::MIN` |
| `newNegUnitX` | - | `vec2` | 构造C++中的 `Vec2::NEG_UNIT_X` |
| `newNegUnitY` | - | `vec2` | 构造C++中的 `Vec2::NEG_UNIT_Y` |
| `newOne` | - | `vec2` | 构造C++中的 `Vec2::ONE` |
| `newUnitY` | - | `vec2` | 构造C++中的 `Vec2::UNIT_Y` |
| `newUnitX` | - | `vec2` | 构造C++中的 `Vec2::UNIT_X` |
| `newZero` | - | `vec2` | 构造C++中的 `Vec2::ZERO` |

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `get` | - | `number`, `number` | 获取存储的xy值 |

###### 元方法

| 函数 | 用途 |
| --- | --- |
| `__tostring` | 调用C++中的 `Vec2::toString` |
| `__add` | 调用C++中的 `Vec2::operator+` |
| `__sub` | 调用C++中的 `Vec2::operator-` |
| `__eq` | 调用C++中的 `Vec2::operator==` |

##### blockinfo

+ 方块信息

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `getName` | - | `string` | 获取游戏内显示的方块名称 |
| `getType` | - | `string` | 获取方块标准类型名 |
| `getId` | - | `integer` | 获取方块的游戏内id |
| `getPos` | - | `blockpos` | 获取方块所在坐标 |
| `getDim` | - | `integer` | 获取方块所在维度ID |
| `getVariant` | - | `integer` | 获取方块特殊值 |
| `getTranslucency` | - | `number` | 获取方块透明度 |
| `getThickness` | - | `number` | 获取方块厚度 |
| `isAir` | - | `boolean` | 方块是否为空气 |
| `isBounceBlock` | - | `boolean` | 是否为可弹跳方块 |
| `isButtonBlock` | - | `boolean` | 是否为按钮方块 |
| `isCropBlock` | - | `boolean` | 是否为农作物方块 |
| `isDoorBlock` | - | `boolean` | 是否为门方块 |
| `isFallingBlock` | - | `boolean` | 是否为可落下的方块 |
| `isFenceBlock` | - | `boolean` | 是否为栅栏方块 |
| `isFenceGateBlock` | - | `boolean` | 是否为栅栏门方块 |
| `isSlabBlock` | - | `boolean` | 是否为半砖方块 |
| `isStemBlock` | - | `boolean` | 是否为干方块 |
| `isThinFenceBlock` | - | `boolean` | 是否为细栅栏方块 |
| `isUnbreakable` | - | `boolean` | 方块是否为不可破坏 |
| `isWaterBlockingBlock` | - | `boolean` | 方块是否可阻挡水 |
| `getNbtTable` | - | `table` | 获取nbt转成的table |
| `getSnbt` | - | `string` | 获取未格式化的Snbt |
| `getSnbtWithPath` | `string` | `string` | 访问特定path的nbt。 `a.b[1].c` 指向根标签下a标签下b数组的第二个元素的c标签 |

###### 元方法

| 函数 | 用途 |
| --- | --- |
| `__eq` | 判断两个 `blockinfo` 是否严格相等 |
| `__gc` | 垃圾回收 |

##### blocksource

+ 代表游戏中的一片区域(Region)，可用于获取指定位置的方块信息

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `getBlockInfo` | `blockpos` | `blockinfo` | 获取指定位置的方块信息 |

##### level

+ 代表游戏存档，可用于获取时间/MSPT信息

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `getDayTime` | - | `integer` | 获取自日出以来的游戏刻 |
| `getGameTime` | - | `integer` | 获取世界总共流逝的游戏刻数 |
| `getDay` | - | `integer` | 获取已流逝的游戏天数 |
| `getMspt` | - | `number` | 获取当前的服务器MSPT信息 |

##### iteminfo

+ 物品信息

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `getName` | - | `string` | 游戏内显示的物品名称 |
| `getType` | - | `string` | 物品标准类型名 |
| `getId` | - | `integer` | 物品的游戏内id |
| `getCount` | - | `integer` | 这个物品对象堆叠的个数 |
| `getAux` | - | `integer` | 物品附加值 |
| `getDamage` | - | `integer` | 物品当前耐久 |
| `getAttackDamage` | - | `integer` | 物品攻击伤害 |
| `getMaxDamage` | - | `integer` | 物品最大耐久 |
| `getMaxStackSize` | - | `integer` | 物品最大堆叠数 |
| `getLore` | - | `table` | 物品的Lore |
| `isArmorItem` | - | `boolean` | 物品是否为盔甲 |
| `isBlock` | - | `boolean` | 物品是否为方块 |
| `isDamageableItem` | - | `boolean` | 物品是否可被破坏 |
| `isDamaged` | - | `boolean` | 物品耐久是否被消耗 |
| `isEnchanted` | - | `boolean` | 物品是否已被附魔 |
| `isEnchantingBook` | - | `boolean` | 物品是否为附魔书 |
| `isFireResistant` | - | `boolean` | 物品是否防火 |
| `isFullStack` | - | `boolean` | 物品是否已堆叠到最大堆叠数 |
| `isGlint` | - | `boolean` | 物品是否闪烁 |
| `isHorseArmorItem` | - | `boolean` | 物品是否为马铠 |
| `isLiquidClipItem` | - | `boolean` | 物品是否能与液体方块交互 |
| `isMusicDiscItem` | - | `boolean` | 物品是否为唱片 |
| `isOffhandItem` | - | `boolean` | 物品是否可设置到副手 |
| `isPotionItem` | - | `boolean` | 物品是否为药水 |
| `isStackable` | - | `boolean` | 物品是否可堆叠 |
| `isWearableItem` | - | `boolean` | 物品是否可穿戴 |
| `getNbtTable` | - | `table` | 获取nbt转成的table |
| `getSnbt` | - | `string` | 获取未格式化的Snbt |
| `getSnbtWithPath` | `string` | `string` | 访问特定path的nbt。 `a.b[1].c` 指向根标签下a标签下b数组的第二个元素的c标签 |

###### 元方法

| 函数 | 用途 |
| --- | --- |
| `__eq` | 判断两个 `iteminfo` 是否严格相等 |
| `__gc` | 垃圾回收 |

##### simplayer

+ 假人对象

###### 对于具体变量 ( `foo:bar()` 调用方式 )

| 函数 | 参数 | 返回 | 用途 |
| --- | --- | --- | --- |
| `getName` | - | `string` | 获取假人真名 |
| `getXuid` | - | `string` | 获取假人XUID |
| `getStatus` | - | `integer` | 获取假人状态 0.离线 1.存活 2.死亡 |
| `getPos` | - | `vec3` | 获取假人眼部位置 |
| `getFeetPos` | - | `vec3` | 获取假人脚部位置 |
| `getStandingOn` | - | `blockpos` | 获取假人所站方块的位置 |
| `getRot` | - | `vec2` | 获取假人视角 |
| `getHealth` | - | `integer` | 获取假人生命值 |
| `getHunger` | - | `number` | 获取假人饥饿值 |
| `sneaking` | `boolean` | `boolean` | 设置假人是否潜行，返回是否成功 |
| `swimming` | `boolean` | - | 设置假人是否游泳/趴下 |
| `attack` | - | `boolean` | 假人攻击，返回是否成功 |
| `chat` | `string` | - | 假人发送消息 |
| `destroy` | - | `boolean` | 假人破坏方块，返回是否成功 |
| `dropSelectedItem` | - | `boolean` | 假人丢出手持物品，返回是否成功 |
| `dropInv` | - | `boolean` | 假人丢出背包（不包括副手、盔甲栏、末影箱）物品，返回是否成功 |
| `runCmd` | `string` | `boolean` | 假人执行指令，返回是否成功 |
| `getBlockPosFromView` | - | `blockpos` | 获取假人视线指向的方块坐标（手长5.25f） |
| `searchInInvWithId` | `integer[, integer]` | `integer` | 在假人背包内搜索给定id的物品，若给出第二个参数则从指定位置开始搜索。返回找到的第一个物品的槽位 |
| `searchInInvWithName` | `string[, integer]` | `integer` | 在假人背包内搜索给定name的物品，若给出第二个参数则从指定位置开始搜索。返回找到的第一个物品的槽位 |
| `selectSlot` | `integer` | `boolean` | 将手持物品与指定槽位物品交换，返回是否成功 |
| `select` | `integer` | `boolean` | 将手持物品与背包内指定id的第一个物品交换，返回是否成功 |
| `getItemFromInv` | `integer` | `iteminfo` | 返回背包内指定槽位的物品信息 |
| `interact` | - | `boolean` | 假人交互，返回是否成功 |
| `jump` | - | `boolean` | 假人跳跃，返回是否成功 |
| `useItem` | `integer` | - | 假人使用物品，并在指定tick后停止使用 |
| `startBuild` | - | - | 假人开始搭建方块 |
| `lookAt` | `vec3` | - | 假人看向指定坐标 |
| `moveTo` | `vec3` | - | 假人移动到指定坐标 |
| `navigateTo` | `vec3` | - | 假人寻路走到指定坐标 |
| `isTaskFree` | - | `boolean` | 假人是否没有在执行动作 |
| `stopAction` | - | - | 停止假人所有动作 |
| `getFirstEmptySlot` | - | - | 获取假人背包内的第一个空位，全满返回-1 |
| `tryPutIntoContainer` | `integer` | `integer` | 将假人背包内指定槽位的物品存放至指向容器。[返回值枚举](https://github.com/CoralFans-Dev/CFSP/blob/develop/src/cfsp/simplayer/CFSP.h#L284) |
| `tryGetFromContainerWithName` | `string` | `integer` | 从指向容器获取一堆指定type的物品。[返回值枚举](https://github.com/CoralFans-Dev/CFSP/blob/develop/src/cfsp/simplayer/CFSP.h#L284) |

###### 元方法

| 函数 | 用途 |
| --- | --- |
| `__gc` | 垃圾回收 |

#### 变量

> 请不要给内置变量重新赋值！

+ `BlockSource` 代表假人所在的一片世界区域，可用于获取指定方块信息
+ `Level` 代表假人所在的存档，可用于获取时间/MSPT信息
+ `SimPlayer` 代表执行脚本的假人对象

### 其他技巧与说明信息

+ 建议在非生产环境测试脚本能用后再部署到实际的服务器中，防止出现未知的错误或者崩溃
+ 您只应上传受信任的脚本供玩家执行
+ 如果发生错误，插件会在服务器内广播错误信息
+ 设定Tick执行间隔的时候优先使用script子命令内的参数，而不是使用脚本内计数器的方案，这样可以降低一定卡顿
+ 暂未性能进行测试，如果发现明显的掉刻，请优化自己编写的脚本，减少函数执行频率，甚至停止脚本的使用
+ 不使用该功能时不会产生任何额外的卡顿
+ 如果发现任何（非编程上的）问题，请前往[GitHub](https://github.com/CoralFans-Dev/CFSP/issues)反馈

### 实例

+ 下面是两个简单的实例，可用于熟悉/测试脚本API

#### 假人播报消息

```lua
function Init(arg) -- 初始化函数
    log(SimPlayer:getName(), SimPlayer:getXuid(), "script test1 run", arg) -- 在控制台输出信息
    return true -- 返回真以继续执行
end

function Tick() -- 循环执行函数
    SimPlayer:chat(string.format("MSPT 是 %.3f",Level:getMspt())) -- 播报mspt
    SimPlayer:chat(string.format("现在的时间是 %d 游戏刻是 %d",Level:getDayTime(),Level:getGameTime())) -- 播报时间
    local x, y, z = SimPlayer:getPos():get() -- 获取眼部坐标
    SimPlayer:chat(string.format("我的坐标是%.3f %.3f %.3f", x, y, z)) -- 播报坐标
    local hungry = SimPlayer:getHunger() -- 获取饥饿值
    local health = SimPlayer:getHealth() -- 获取生命值
    SimPlayer:chat(string.format("我的饥饿度是 %.3f,我的血量是 %d",hungry,health)) -- 播报饥饿值与生命值
    local stand = SimPlayer:getStandingOn() -- 获取所站方块的坐标
    local sx, sy, sz = stand:get() -- 展开具体xyz
    local blockInfo = BlockSource:getBlockInfo(stand) -- 获取所站方块的信息
    SimPlayer:chat(string.format("我站的方块坐标是 %.3f %.3f %.3f 脚底的方块类型是 %s id 是 %d", sx, sy, sz,
        blockInfo:getName(), blockInfo:getId())) -- 播报方块信息
    return true -- 一直返回真，会一直循环执行
end
```

+ 保存脚本至 `plugins/CoralFans/data/simplayer/scripts/test1.lua`
+ 执行指令 `sp p SIM-bot script test1.lua` ，可以让假人 `SIM-bot` 每20gt播报一次信息

#### 假人自动搭高

```lua
TickTime = 0; -- 计时
Stand = nil -- 所站方块位置
Blocks = 0

function Init(arg) -- 初始化函数
    log(SimPlayer:getName(), SimPlayer:getXuid(), "script test2 run", arg) -- 在控制台输出信息
    Stand = SimPlayer:getStandingOn() -- 记录所站方块坐标
    SimPlayer:select(12) -- 选中背包内的沙子
    Blocks = tonumber(arg) -- 获取传入参数
    SimPlayer:lookAt(Stand:center()) -- 看向脚下方块的中心
    SimPlayer:startBuild() -- 开始搭建方块
    return true -- 返回真以继续执行
end

function Tick() -- 循环执行函数
    if TickTime == 20 * Blocks then
        SimPlayer:stopAction() -- 停止操作（搭建方块）
        return false
    end -- 如果执行了20 * Blocks gt，中断
    if TickTime % 20 == 0 then -- 每执行20gt
        Stand = SimPlayer:getStandingOn() -- 记录所站坐标
        SimPlayer:jump() -- 起跳
    end
    SimPlayer:lookAt(Stand:center()) -- 看向脚下方块的中心
    TickTime = TickTime + 1 -- 计时器+1
    return true -- 返回真以执行下一次
end
```

+ 保存脚本至 `plugins/CoralFans/data/simplayer/scripts/test2.lua`
+ 执行指令 `sp p SIM-bot script test2.lua 1 10` ，可以让假人 `SIM-bot` 用背包里的沙子原地搭高10个方块
