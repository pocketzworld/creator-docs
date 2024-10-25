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

### Examples:

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

Assuming you have a timer thats running for 5 seconds and you want to stop and clear it after:
```lua
-- Local variable to store the timer
local interval = nil

-- Function to reset the interval
local function ResetInterval()
    if interval then
        interval:Stop()
        interval = nil
    end
end

--[[
    Function to run a timer for a specified number of seconds
    @param seconds: number
]]
function RunInterval(seconds: number)
    -- Always reset the timer before starting it
    ResetInterval()

    interval = Timer.Every(seconds, function()
        -- Check if the interval is still running
        if interval == nil then return end
        -- Your logic here
    end)
end


-- You can call the RunInterval function to start the timer
-- RunInterval(5)

-- You can call the ResetInterval function to stop the timer
-- ResetInterval()
```

By harnessing the power of timers, you can efficiently manage time-sensitive tasks and create engaging and dynamic gameplay experiences.
