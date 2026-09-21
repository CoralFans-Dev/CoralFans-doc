# CFSP DLL API DOC

## DLLAPI

### xmake configuration

1. Import the required libraries in order
2. Add the dependencies inside the target
3. Include the header file and you're ready to use it

Here is an example of importing the required libraries

```lua
add_requires("levilamina", "timewheel", "CFSP")
```

### Header files

+ You need to use `cfsp/core/simPlayer/SimPlayer.h`. Functions/data defined in other header files are not exported via dllexport.
+ All exported functions are marked with `CFSP_API`. You can check [src/cfsp/core/simPlayer/SimPlayer.h](https://github.com/CoralFans-Dev/CFSP/blob/develop/src/cfsp/core/simPlayer/SimPlayer.h) to see which functions you can call.
+ Most function definitions are fairly easy to understand. You can look at how the command system calls them to understand what these functions mean.
+ Additionally, we provide some interfaces to obtain the `SimPlayer` and related information.
+ Some member functions of `SimPlayer` will throw an error when the pointer they hold to the in-game simulated player is null.
+ Most functions return a value of type `base::OperateResult`; see [src/cfsp/base/OperateResult.h](https://github.com/CoralFans-Dev/CFSP/blob/develop/src/cfsp/base/OperateResult.h) for its enum values.
