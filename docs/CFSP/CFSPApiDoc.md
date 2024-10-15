# CFSP DLL API DOC

## DLLAPI

### xmake配置

1. 按顺序导入相关库
2. 在target内添加依赖
3. 引入头文件即可使用

以下是导入相关库的例子

```lua
add_requires("boost", {configs = {all = true}})
add_requires("levilamina", "timewheel", "CFSP")
```

### 头文件

+ 一般地，您仅需要使用 `cfsp/simplayer/CFSP.h` 。其他头文件定义的函数/数据并没有通过dllexport导出。
+ 所有导出的函数都由 `CFSP_API` 标记。您可以查阅[src/cfsp/simplayer/CFSP.h](https://github.com/CoralFans-Dev/CFSP/blob/develop/src/cfsp/simplayer/CFSP.h)来查看您可以调用哪些函数。
+ 大部分函数的定义都是比较易懂的。你可以看指令系统是如何调用的来理解这些函数的意义。
+ 额外地，我们提供了一些接口以获取 `SimPlayerInfo` 以及相关信息。
+ `SimPlayerInfo` 的部分成员函数在自身指向游戏中假人的指针为空时会抛出错误。
