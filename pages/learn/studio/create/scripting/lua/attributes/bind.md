# Bind

Using the `Bind` attribute, you can associate a Lua variable with a UI element, such as a text label, image, button, or input field. This feature enables you to synchronize data between your Lua script and the UI elements in your game, creating dynamic and interactive user interfaces.

## How to Bind UI Elements

To bind a UI element to a Lua variable, you need to use the `Bind` attribute followed by the variable declaration. This attribute tells the Studio Editor to display the variable in the Inspector panel and link it to the specified UI element.

Here's an example of binding a UI element to a Lua variable:

```lua
--!Bind
local myLabel : UILabel = nil

myLabel:SetPrelocalizedText("I am a UILabel")
```

In this example, `myLabel` is a Lua variable bound to a `UILabel` UI element. By adding the `Bind` attribute before the variable declaration, you can link `myLabel` to the `UILabel` UI element in the Inspector panel.

The `myLabel` variables must match the type of the UI element you want to bind. For example, if you want to bind a text label, you should use the `UILabel` type. Similarly, for an image, you should use the `UIImage` type.

```html
<hr:UILuaView class="my-ui" picking-mode="Ignore">
    <hr:UILabel name="myLabel" picking-mode="Ignore">
    </hr:UILabel>
</hr:UILuaView>
```

In this example you can see the `UILabel` element with the name `myLabel` that is bound to the `myLabel` variable in the Lua script.

## Conclusion

By using the `Bind` attribute, you can establish a connection between Lua variables and UI elements in your game. This feature simplifies the process of managing and updating UI elements, enabling you to create dynamic and interactive user interfaces that enhance the player experience.