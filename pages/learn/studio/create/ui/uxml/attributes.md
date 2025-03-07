# UXML Attributes

## Introduction

Attributes are used to define the properties of a UXML element. They are key-value pairs that are used to set the appearance, behavior, and other properties of the element. Attributes are defined within the opening tag of an element and are separated by spaces.

## Syntax

The general syntax for defining attributes in UXML is as follows:

```xml
<VisualElement attribute1="value1" attribute2="value2" />
```

In the above syntax:

- `VisualElement` is the name of the UXML element.
- `attribute1` and `attribute2` are the attribute names.
- `value1` and `value2` are the values assigned to the attributes.

## Common Attributes

Here are some common attributes used in UXML:

### name

The `name` attribute serves as an identifier for the element and should be unique. It is often used for binding the element with Lua scripts.

Example:

```xml
<VisualElement name="uniqueElement" />
```

In this example, the `name` attribute is set to `uniqueElement`, which can be used to reference this element in Lua scripts.

Example:

You can bind the element in Lua using the following syntax `--!Bind`:
```lua
--!Bind 
local uniqueElement : VisualElement = nil
```

uniqueElement is now bound to the VisualElement with the name "uniqueElement".

### class

The `class` attribute is used to assign a CSS class to the element. It allows you to style the element using CSS.

Example:

```xml
<VisualElement class="button" />
```

You can assign multiple classes to an element by separating them with spaces:

```xml
<VisualElement class="button selected" />
```

And later access them using CSS:

```css
.button {
  background-color: blue;
}

.selected {
  background-color: red;
}
```

When an element has multiple classes, the styles are applied in the order they are defined in the `class` attribute.

### picking-mode

The `picking-mode` attribute defines how the element interacts with mouse events. It can have the following values:

- `Ignore`: The element does not respond to mouse events.
- `Position`: The element responds to mouse events based on its position.

Example:

```xml

<Button class="action-button" name="clickButton" />
<VisualElement picking-mode="Ignore" />
```

If `picking-mode` is `Ignore`, the element will not respond to mouse events.

### tooltip

The `tooltip` attribute provides additional information when the user hovers over the element.

Example:

```xml
<Button text="Hover me" tooltip="This is a button" />
```

The tooltip will be displayed when the user hovers over the element.

## Conclusion

Attributes are an essential part of UXML elements as they define the properties and behavior of the elements. By using attributes, you can customize the appearance and behavior of your UI elements to create a rich user experience.
