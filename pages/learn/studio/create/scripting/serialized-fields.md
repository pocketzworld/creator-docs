# **Serialized Fields**

## **Introduction**
In this guide you will learn how to create Serialized Fields to expose your variables to the Editor.

### **What is a Serialized Field?**
A Serialized Field is what we call a Lua variable that has been Serialized and Typed, making it available to control in the Editor.

![Properties](/assets/learn/guides/studio/properties.png)

Highrise Studio uses Lua for scripting,
Therefore variables are declared as follows.
``` lua
local myNumber = 5
local myString = "Hi There"
local myBool = true
```

Variables defined this way are not visible in the Inspector.
To access variables via the Editor they need to be in a `SerializeField` as well as `Typed`
When you `Type` a variable you have the fundamental types `number` `boolean` `string` as well as Unity's built in Types such as: `GameObject` `Transform` and `Vector3`
``` lua
--!SerializeField
local myNumber : number = 0
--!SerializeField
local myString : string = "default"
--!SerializeField
local myBool : boolean = true
--!SerializeField
local myGameObject : GameObject = nil
--!SerializeField
local myTransform : Transform = nil
--!SerializeField
local myVector : Vector3 = Vector3.new()
```
>Note: when declaring typed variables, the fundamental types are `lowercase` where the Unity types are `PascalCase`.
>To get more supported Unity Types, see `Learn>Studio>API>Classes` on the Create Portal.