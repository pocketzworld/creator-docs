# UXML Overview

## Introduction

**UXML** (Unity Extensible Markup Language) is a markup language used in Unity to define the structure of user interfaces. It is similar to XML and HTML, making it easy to understand and use. UXML allows developers to create and organize UI elements in a structured and hierarchical manner.

## Key Features
- **Structured Layout**: UXML provides a way to define the structure of your UI in a clear and organized manner, similar to how HTML is used for web development.
- **Reusability**: You can create reusable UI components, making it easier to maintain and scale your project.
- **Flexibility**: UXML works seamlessly with USS (Unity Style Sheets) for styling and Lua for adding functionality.

## Example: A Basic UXML Structure

Below is an example of a simple **UXML** file used in **Highrise Studio**:

```xml
<?xml version="1.0" encoding="utf-8"?>
<UXML
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="UnityEngine.UIElements"
    xmlns:hr="Highrise.UI"
    xmlns:editor="UnityEditor.UIElements"
    xsi:noNamespaceSchemaLocation="../../../../UIElementsSchema/UIElements.xsd"
>

  <hr:UILuaView class="dropdown">
    <VisualElement class="button plus">
      <Image class="icon plus" />
    </VisualElement>
  </hr:UILuaView>

</UXML>
```

### Breakdown of the Example:
- The **`<UXML>`** root element defines the document structure.
- The **`xmlns`** attributes specify namespaces to reference UI elements from **Unity**, **Highrise**, and **Unity Editor**.
- The **`<hr:UILuaView>`** element represents a custom UI component defined in Highrise, styled with the **`dropdown`** class.
- Inside it, a **`<VisualElement>`** acts as a button (styled with **`button plus`**).
- The **`<Image>`** element within the button represents an icon (styled with **`icon plus`**).

## Getting Started with UXML
To begin using **UXML**:
1. **Define the UI structure**: Create a UXML file and define UI elements as seen in the example.
2. **Style with USS**: Use Unity Style Sheets to style elements and ensure consistency across your UI.
3. **Add Functionality with Lua**: Use Lua scripting to handle interactions and dynamic UI updates.

## Further Reading
For more detailed information, refer to the [Unity UXML documentation](https://docs.unity3d.com/Manual/UIE-UXML.html).

In the next sections, we'll explore **USS for styling** and **Lua for scripting UI interactions**.