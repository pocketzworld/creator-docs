# UXML Elements

## Introduction

UXML elements are the building blocks of user interfaces in Unity. Each element represents a specific UI component, and they can be nested to create complex interfaces. Elements can either be self-closing or contain other elements.

## Common UXML Elements

### VisualElement
The `VisualElement` is the base class for all UI elements. It can be used as a container for other elements or as a standalone UI component.

Example:
```xml
<VisualElement class="container">
  <!-- Other elements go here -->
</VisualElement>
```

### Highrise.UI.LuaView
The `UILuaView` element is a custom Highrise component used to integrate Lua functionality with UI elements.

Example:
```xml
<hr:UILuaView class="dropdown">
  <VisualElement class="button">
    <Image class="icon" />
  </VisualElement>
</hr:UILuaView>
```

### Highrise.UI.ScrollView
The `UIScrollView` allows for scrollable content within a UI. It is useful for displaying large amounts of content in a limited space.

Example:
```xml
<hr:UIScrollView class="scroll-area">
  <!-- Scrollable content goes here -->
</hr:UIScrollView>
```

### Label
The `Label` element is used to display text within the UI.

Example:
```xml
<Label text="Hello, World!" class="greeting" />
```

### Button
The `Button` element creates a clickable button for user interactions.

Example:
```xml
<Button text="Click Me" class="action-button" />
```

### Image
The `Image` element is used to display images within the UI.

Example:
```xml
<Image class="icon-image" />
```

## Attributes

UXML elements can have various attributes that define their properties and behavior. Here are some important ones:

### name
The `name` attribute serves as an identifier for the element and should be unique. It is often used for binding the element with Lua scripts.

Example:
```xml
<VisualElement name="uniqueElement" />
```

## Class Attribute
The `class` attribute is a space-separated list of identifiers that categorize the element. Classes are used to assign visual styles to elements.

Example:
```xml
<VisualElement class="container highlighted" />
```


### picking-mode
The `picking-mode` attribute controls how the element interacts with user input. Setting it to "Ignore" makes the element non-interactable, useful for cases where elements overlap.

Example:
```xml
<VisualElement picking-mode="Ignore" />
```

### tooltip
The `tooltip` attribute provides additional information when the user hovers over the element.

Example:
```xml
<Button text="Hover me" tooltip="This is a button" />
```

## Conclusion
Understanding UXML elements and their attributes is crucial for building effective user interfaces in Unity. By mastering these elements and attributes, you can create complex and dynamic UIs for your projects.

In the next sections, we'll delve deeper into each element and provide detailed usage examples.