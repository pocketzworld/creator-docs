# **Lifecycle Functions**

## **Introduction**
In this guide you will learn how to connect to the built in Unity Lifecycle Functions with your lua script.

### **What is a Lifecycle Function?**
Life Cycle Functions are special functions that are automatically called at specific intervals of an Object's or Component's Lifetime

![LifeCycle](/assets/learn/guides/studio/lifecycle.png)

**Initialization Events**
- Initializattion events are called before any updates.
- The Start function is called before any physics update and before the first frame, while the Awake function is called for each object in the scene when calling up a scene.

- Start and Awake functions for different objects are called in a random order, but all Awake calls are finished before any Start is called.
>Note: This means trying to reference other objects in the Awake state is unstable as the Objects may not be `Initialized` yet.
>Objects outside of a script are best defined in the `Start` function.

**Game Logic Events**
- The Game Logic Events include the Realtime functions and loops namely `Update`, `OnTriggerEnter`, and `OnTriggerExit`.

**Deconstruction Events**
- Deconstruction events are called in all activated objects in a scene.
- The OnDisable function is called when a given object is disabled or is inactive.

>❗️ALERT
>Unlike Unity, Highrise does not have an Awake function. Code that you would typically place in the Awake function is placed within the Lua script outside of any function, which Highrise will execute immediately when the script loads.

### Below is an example script with supported LifeCycle functions:

```lua
function self:Start()
    print("I started. This is still the first frame I am alive!")
end

function self:Update()
    print("This frame took " .. Time.deltaTime .. "seconds")
end

function self:LateUpdate()
    print("This frame took " .. Time.deltaTime .. "seconds, but I'm happening after all the other normal Updates occured")
end

function self:FixedUpdate()
    print("This physics step took " .. Time.fixedDeltaTime .. " seconds and will always take that long, unless manually changed")
end

function self:OnTriggerExit(other : Collider)
    print("This triggering collider left: " .. other.gameObject.name)
end

function self:OnTriggerStay(other : Collider)
    print("The triggering collider that has not left is named " .. other.gameObject.name)
end

function self:OnTriggerEnter(other : Collider)
    print("I was triggered by a collider named " .. other.gameObject.name)
end

function self:OnCollisionExit(collision : Collision)
    print("I stopped colliding with and touching a collider named " .. collision.gameObject.name)
end

function self:OnCollisionStay(collision : Collision)
    print("I am still colliding with and touching a collider named " .. collision.gameObject.name)
end

function self:OnCollisionEnter(collision : Collision)
    print("I collided with a collider named " .. collision.gameObject.name)
end
```

You can learn more about Unity's Event Functions here.
> 📖 [Unity Docs Execution Order.](https://docs.unity3d.com/2022.3/Documentation/Manual/ExecutionOrder.html)