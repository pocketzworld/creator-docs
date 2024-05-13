# **Timers**

## **Introduction**
Timers are objects designed to execute specified functions after a defined interval of time. They are seamlessly integrated into the behavior they were created in, ensuring automatic destruction if the associated behavior is destroyed. Timers offer flexibility in scheduling tasks, whether it's a one-time event or a recurring action.



### **Timer Types**

`Timer.new(interval, callback, repeat)`  
Create a new timer that triggers the specified callback function after a given interval. Optionally, it can repeat the execution.

`Timer.Every(interval, callback)`  
Establish a timer that invokes the provided callback function at regular intervals. It can be halted explicitly or automatically stopped if the associated behavior is destroyed.

`Timer.After(interval, callback)`  
Set up a timer that fires the callback once after the specified interval.


### **Timer Functions**

`timer:Stop()`  
Halt a running timer.

`timer:Start()`  
Resume a previously stopped timer from where it left off.

`timer:Restart()`  
Reset a timer to its initial state, effectively restarting its interval. If stopped, it will automatically resume.

### Example:

Here's an example demonstrating how to create and run Timers in Lua:
```lua
function self:Awake()
    -- Create a new Timer object. Interval: 5, Callback:function()..end, Repeating: false
    local newTimer = Timer.new(5, function() print("newTimer just finished") end, false)

    -- Call the After function to immediately connect to a non repeating Timer
    Timer.After(10, function() 
        print("10s has passed. restarting newTimer") 
        newTimer:Restart() -- Restart our Timer Object "newTimer"
    end)

    -- Call the Every function to immediately connect to a repeating Timer
    Timer.Every(20, function() print("20s has passed... restarting 20s timer...") end)
end
```

By harnessing the power of timers, you can efficiently manage time-sensitive tasks and create engaging and dynamic gameplay experiences.
