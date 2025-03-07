# Classes in USS

## Introduction

Classes in USS allow you to style multiple elements at once by assigning them a shared class name. They work similarly to CSS, making it easy to reuse styles, organize UI, and control element appearance dynamically.

## Defining and Applying Classes

To assign a class to an element, use the `class` attribute in UXML.

### Example (UXML)
```xml
<VisualElement class="container" />
<Label class="title" text="Hello, World!" />
```

### Example (USS)
```css
.container {
    background-color: #f0f0f0;
    padding: 10px;
}

.title {
    font-size: 18px;
    color: black;
}
```
Any element with the `container` class will get a gray background and padding.

## Targeting Elements with Classes

You can target specific elements inside a class using nested selectors.

### Example: Targeting a Specific Element
```xml
<VisualElement class="close-button">
    <Image class="icon" />
</VisualElement>
```

```css
.close-button Image {
    width: 20px;
    height: 20px;
    --unity-image: var(--image-icon-close);
}
```
This targets the `<Image>` inside `.close-button` and resizes it.

## Targeting Named Elements with `#nameHere`

If an element has a `name` attribute, you can reference it directly in USS using `#nameHere`.

### Example (UXML)
```xml
<Button name="submitButton" text="Submit" />
```

### Example (USS)
```css
#submitButton {
    background-color: blue;
    color: white;
}
```
This targets only the button with `name="submitButton"`, regardless of class.

## Using Nested Selectors (`.container .header`)

Nested selectors allow styling elements within a specific parent.

### Example (UXML)
```xml
<VisualElement class="container">
    <VisualElement class="header">
        <Label text="Title" />
    </VisualElement>
</VisualElement>
```

### Example (USS)
```css
.container .header {
    background-color: lightgray;
}
```
This only applies the background color to `.header` when it is inside `.container`.

## Using State-Based Selectors (`.button.enabled`)

USS allows styling elements based on multiple classes.

### Example (UXML)
```xml
<Button class="button enabled" text="Click Me" />
```

### Example (USS)
```css
.button.enabled {
    background-color: green;
}
```
The button will only turn green if it has both `button` and `enabled` classes.

## Selecting Multiple Elements at Once (`.button-primary, .button-secondary`)

You can apply styles to multiple elements using a comma-separated list.

### Example (UXML)
```xml
<Button class="button-primary" text="Primary" />
<Button class="button-secondary" text="Secondary" />
```

### Example (USS)
```css
.button-primary, .button-secondary {
    padding: 10px;
    font-size: 16px;
}
```
Both `.button-primary` and `.button-secondary` share the same styles.

## Using `:hover` for Interactive Effects

USS allows hover effects to provide feedback when users interact with elements.

### Example (UXML)
```xml
<Button class="clickable" text="Hover Me" />
```

### Example (USS)
```css
.clickable {
    background-color: blue;
    color: white;
}

.clickable:hover {
    background-color: darkblue;
}
```
When the user hovers over the button, the background color changes.

## Conclusion

Classes in USS streamline UI styling by grouping elements with shared styles. By defining, targeting, and applying classes effectively, you can create a consistent and visually appealing user interface.