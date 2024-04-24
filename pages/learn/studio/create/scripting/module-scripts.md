# **Module Scripts**

## **Introduction**
Module scripts in Highrise Studio serve as reusable pieces of code that can be accessed from various parts of your project. They help maintain organized and efficient code by allowing you to define functions, variables, or even configurations in one script and use them across multiple other scripts.

### **Creating a Module Script**
To create a module script, simply create a new Lua script and set the script type to `module`. This script will run on its own as well as act as a library for other scripts.

> Note:  
>`module` scripts, like `client/server` scripts run on both the `client` and `server`.  
>This will allow use of client/server functions: `ClientAwake()`,`ServerAwake()`, etc.

**Example:**
```lua
-- In MyModuleScript
number = 10
message = "Hello, this is a module script!"

function addNumbers(a, b)
    return a + b
end
```
### **Using a Module Script**
To use a module script, initialize it by putting it on an object in the hierarchy then require it in another script using the `require` function. This allows you to access any non-local variable or function defined in the module script.
**Example:**
```lua
-- In another Client and/or Server script
local MyModule = require("MyModuleScript") -- Replace "MyModuleScript" with the name of your module script

print(MyModule.message) -- Outputs: Hello, this is a module script!
local sum = MyModule.addNumbers(5, 7)
print("The sum is " .. tostring(sum)) -- Outputs: The sum is 12
```

**Benefits of Using Module Scripts**
- Code Reusability: Define code once and use it in multiple scripts throughout your project.
- Cleaner Codebase: Helps keep your codebase cleaner and more organized by separating functionality.
- Easier Maintenance: Changes in the module script reflect across all scripts that require it, making it easier to maintain and update code.

By utilizing module scripts, you can streamline your development process in Highrise Studio, ensuring that your code remains modular, maintainable, and efficient.
