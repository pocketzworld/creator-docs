# Unity Style Sheets (USS) Overview

## Introduction

Unity Style Sheets (USS) are used to define the **visual styling** of UI elements within Unity’s **UI Toolkit**. Inspired by CSS, USS allows developers to **separate structure from appearance**, making UI easier to maintain and modify.

## Syntax and Structure

USS files use a syntax similar to CSS, allowing developers to **define styles for UI elements** using class selectors.

**Example:**
```css
/* Define a style for buttons */
.button {
    background-color: #3498db;
    color: white;
    padding: 10px;
    border-radius: 5px;
}

/* Define a style for labels */
.label {
    font-size: 14px;
    color: #333;
}
```
In this example:
- The `.button` class **sets the background color, text color, padding, and rounded corners**.
- The `.label` class **controls font size and color**.

### Using Multiple Classes
You can assign **multiple classes** to a single UI element by **separating them with spaces**.

**Example (UXML):**
```xml
<Button class="button primary" text="Click Me" />
```

**USS Styles:**
```css
.button {
    background-color: #3498db;
    color: white;
}

.primary {
    border: 2px solid white;
}
```
💡 Since `.primary` is applied **in addition** to `.button`, it **adds a white border** without overriding other styles.

## Hover Effects

USS allows styling elements based on **hover interactions**, enhancing **UI feedback**.

**Example:**
```css
.button:hover {
    background-color: #2980b9;
}
```
When the user **hovers** over an element with the `.button` class, its **background color changes**.


## Changing Styles Dynamically with Lua

While USS is static, some **styles can be changed dynamically using Lua**.

**Example (Lua):**
```lua
--!Bind
local myButton : Button = nil

myButton:AddToClassList("highlighted") -- Adds a new class
myButton:RemoveFromClassList("primary") -- Removes an existing class
```
**Example USS:**
```css
.highlighted {
    background-color: yellow;
}
```
💡 This allows you to **toggle styles dynamically** based on user interactions or game events.

## Common USS Properties

USS supports many properties for styling UI elements. Some of the most commonly used include:

| Property           | Description |
|--------------------|-------------|
| `background-color` | Sets the background color. |
| `color`           | Defines text color. |
| `padding`         | Controls spacing inside the element's border. |
| `margin`          | Sets spacing outside the element. |
| `border-radius`   | Determines the roundness of corners. |
| `font-size`       | Sets text size. |
| `width`, `height` | Defines the element's dimensions. |

For a full list, see [USS Properties Reference](https://docs.unity3d.com/6000.0/Documentation/Manual/UIE-USS-Properties-Reference.html).

## Conclusion

- **USS helps separate structure from styling**, making UI maintenance easier.
- **Multiple classes** can be applied to elements for modular styling.
- **Hover effects** provide interactive feedback.
- **Lua scripting** can be used to **change styles dynamically**.

By following these practices, you can build **scalable and maintainable UI layouts** in Unity.