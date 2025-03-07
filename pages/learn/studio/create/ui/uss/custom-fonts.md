# Using Custom Fonts in Unity UI

## Introduction

Fonts play a key role in UI design by conveying information, setting tone, and improving aesthetics. In Unity, custom fonts allow you to create a unique user interface that aligns with your project's style.

## Importing Custom Fonts

### Step 1: Choose and Download a Font
1. Select a font that matches your project's style.  
   - Fonts can be found on platforms like Google Fonts, Adobe Fonts, or commercial libraries.
2. Ensure you have the necessary licensing rights before using the font.
3. Download the font file in `.ttf` or `.otf` format.

### Step 2: Import the Font into Unity
1. Create a **Fonts** folder in your project to keep assets organized.
2. Drag and drop the font file into the Fonts folder.
3. Convert the font to a Unity asset:  
   - Right-click the font file → `Create` > `Text` > `Font Asset`.  
   - Unity will generate a `.asset` file optimized for UI elements.

<Note type="warning">
Ensure you have the necessary licensing rights to use the font in your project.
</Note>

## Using Custom Fonts in Unity UI

### Step 1: Define the Font in USS
To apply the font in USS, use the `-unity-font-definition` property.

#### Example (USS)
```css
.text-style {
    -unity-font-definition: url("project://database/Assets/UI/Fonts/custom-font.asset");
}
```
<Note type="warning">
Ensure the font path in USS matches the actual font location in your Unity project.
</Note>

### Step 2: Apply the Font in UXML
Once defined in USS, apply the font style in UXML.

#### Example (UXML)
```xml
<Label class="text-style" text="Hello, World!" />
```
This applies the custom font to the `Label` element.

## Conclusion

Custom fonts improve UI aesthetics and branding in Unity. By importing, defining, and applying fonts correctly, you can create a visually appealing and consistent interface. Ensure fonts are readable and comply with licensing requirements.