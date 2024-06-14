# Lifecycle Functions

## Introduction
In this guide, you will learn about Unity's Lifecycle Functions and how they can be used to create dynamic and interactive experiences in your Highrise Studio projects.

## What is a Lifecycle Function?
Life Cycle Functions are special functions that are automatically called at specific intervals of an Object's or Component's Lifetime.

In Unity, these functions are called at specific points in the game's execution cycle, such as when an object is created, updated, or destroyed. By using these functions, you can control the behavior of your objects and components at different stages of their life cycle.

> The image below shows the order in which Unity's Lifecycle Functions are called during the execution of a game.

![LifeCycle](/assets/learn/guides/studio/basics/unity-life-cycle.png)

## Lifecycle Stages

<Note type="warning">
When using `ClientAndServer` type script in Highrise Studio, the functions must be defined as `self:Client[FunctionName]` or `self:Server[FunctionName]` to work properly.
For example, `self:Awake()` should be defined as `self:ClientAwake()` or `self:ServerAwake()`.
</Note>

### Initialization Events

- **Awake()**
  - Called for each object in the scene when calling up a scene.
  - Order of calls is random.
  - Note: Referencing other objects may be unstable since the Objects may not be `Initialized` yet.
- **Start()**
  - All `Awake` calls are finished before any `Start` is called.
  - Best for defining objects outside of a script.
  - Called before any physics update and before the first frame.

**Example Usage:**
```lua
function self:Awake()
    print("Awake called: Initializing object.")
end

function self:Start()
    print("Start called: Object is ready to be used.")
end
```

#### Why do we need both `Awake` and `Start` functions?
The `Awake` function is used to initialize variables or objects that are needed for the script to function properly. Without this function, initialization happens later, which can lead to errors or unexpected behavior if other parts of the game rely on initialization being done earlier. So, skipping the `Awake` step means there's no guarantee that the object is ready to be used.

The `Start` function is used to initialize objects that are not needed for the script to function properly. This function is called after all `Awake` functions have been called, so it's a good place to set up objects that are not needed for the script to function properly.

### Game Logic Events

- **Update()**
  - Called once per frame.
  - Best for regular updates like moving objects.
  - Note: Good for setting up timers.
- **FixedUpdate()**
  - Called at a fixed rate independent of frame rate.
  - Best for physics updates.
- **LateUpdate()**
  - Called after all `Update` functions have been called.
  - Best for camera following or procedural animations.

**Example Usage:**
```lua
function self:Update()
    print("Update called: This frame took " .. Time.deltaTime .. "seconds")
end

function self:FixedUpdate()
    print("FixedUpdate called: This physics step took " .. Time.fixedDeltaTime .. " seconds")
end

function self:LateUpdate()
    print("LateUpdate called: This frame took " .. Time.deltaTime .. "seconds, but I'm happening after all the other normal Updates occured")
end
```

#### Why do we need `Update`, `FixedUpdate`, and `LateUpdate` functions?

The `Update` function is called once per frame and is best for regular updates like moving objects. It's called every frame, so it's a good place to put code that needs to run every frame.

The `FixedUpdate` function is called at a fixed rate independent of the frame rate. It's best for physics updates because physics calculations are more accurate when they're done at a fixed rate.

The `LateUpdate` function is called after all `Update` functions have been called. It's best for camera following or procedural animations because it's called after all the other normal updates have occurred.

### Trigger Events

- **OnTriggerEnter()**
  - Triggered when a collider enters the trigger.
- **OnTriggerStay()**
  - Triggered while a collider stays within the trigger.
- **OnTriggerExit()**
  - Triggered when a collider exits the trigger.
  
<Note type="warning">
The trigger or the collider interacting with it must have a Rigidbody component attached. However, the Rigidbody can be set to kinematic to disable physics simulation.
</Note>

**Example Usage:**
```lua
function self:OnTriggerEnter(other : Collider)
    local enteringGameObject = other.gameObject
    print(enteringGameObject.name .. " has entered the trigger")
end

function self:OnTriggerExit(other : Collider)
    local exitingGameObject = other.gameObject
    print(exitingGameObject.name .. " has left the trigger")
end
```

#### Why do we need `OnTriggerEnter`, `OnTriggerStay`, and `OnTriggerExit` functions?

The `OnTriggerEnter` function is triggered when a collider enters the trigger. It's best for detecting when an object enters a trigger and reacting to it.

The `OnTriggerStay` function is triggered while a collider stays within the trigger. It's best for detecting when an object is inside a trigger and reacting to it.

The `OnTriggerExit` function is triggered when a collider exits the trigger. It's best for detecting when an object leaves a trigger and reacting to it.

### Collision Events

- **OnCollisionEnter()**
  - Triggered when a collider enters the trigger.
- **OnCollisionStay()**
  - Triggered while a collider stays within the trigger.
- **OnCollisionExit()**
  - Triggered when a collider exits the trigger.

<Note type="warning">
Both colliders must have a Rigidbody component attached.
</Note>

**Example Usage:**
```lua
function self:OnCollisionEnter(collision : Collision)
    local enteringGameObject = collision.gameObject
    print(enteringGameObject.name .. " has collided with the object")
end

function self:OnCollisionExit(collision : Collision)
    local exitingGameObject = collision.gameObject
    print(exitingGameObject.name .. " has stopped colliding with the object")
end
```

#### Why do we need `OnCollisionEnter`, `OnCollisionStay`, and `OnCollisionExit` functions?

The `OnCollisionEnter` function is triggered when a collider enters the trigger. It's best for detecting when an object collides with another object and reacting to it.

The `OnCollisionStay` function is triggered while a collider stays within the trigger. It's best for detecting when an object is colliding with another object and reacting to it.

The `OnCollisionExit` function is triggered when a collider exits the trigger. It's best for detecting when an object stops colliding with another object and reacting to it.

### Deconstruction Events

- **OnDisable()**
  - Called when the object is disabled or inactive.
  - Best for cleaning up references or stopping coroutines.
- **OnDestroy()**
  - Called when the object is destroyed.
  - Best for cleaning up references or saving data.
  
**Example Usage:**
```lua
function self:OnDisable()
    print("OnDisable called: Object is disabled or inactive.")
end

function self:OnDestroy()
    print("OnDestroy called: Object is destroyed.")
end
```

#### Why do we need `OnDisable` and `OnDestroy` functions?

The `OnDisable` function is called when the object is disabled or inactive. It's best for cleaning up references or stopping coroutines that are no longer needed.

The `OnDestroy` function is called when the object is destroyed. It's best for cleaning up references or saving data that needs to be saved before the object is destroyed.

## Additional Resources

If you are looking for more information on Unity's Lifecycle Functions, you can refer to the [Unity Documentation](https://docs.unity3d.com/2022.3/Documentation/Manual/ExecutionOrder.html).

## Conclusion

By utilizing Unity's Lifecycle Functions effectively, you can create dynamic and engaging experiences for players in your Highrise Studio projects.
