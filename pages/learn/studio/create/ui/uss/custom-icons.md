# Using Custom Icons in Unity UI

## Introduction

Icons help users quickly identify actions, features, or sections within a UI. Well-designed icons improve usability, navigation, and aesthetics.

In Unity, custom icons allow you to create a visually distinct interface. This guide explains how to import, define, and apply custom icons in USS and UXML.

## Importing Custom Icons

### Step 1: Prepare Your Icons
1. Create or download icons in **PNG, SVG, or JPEG** format.
2. Keep icons **simple, clear, and consistent**.
3. Organize assets by creating a dedicated `Icons` folder in Unity.

### Step 2: Import Icons into Unity
1. Drag and drop the icon files into your `Icons` folder in Unity.
2. Adjust import settings:
   - **Texture Type** → `Sprite (2D and UI)`
   - **Compression** → Optimize for performance
   - **Max Size** → Adjust based on UI needs

## Using Custom Icons in USS

### Step 1: Define Icon Classes in USS
USS allows setting icons as background images for UI elements.

#### Example (USS)
```css
.icon-home {
    background-image: url("project://database/Assets/UI/Icons/home.png");
    width: 32px;
    height: 32px;
}

.icon-settings {
    --unity-image: url("project://database/Assets/UI/Icons/settings.png");
    width: 32px;
    height: 32px;
}
```
This defines two classes, `.icon-home` and `.icon-settings`, each applying an icon as a background image.

### Step 2: Apply Icons in UXML
Once defined in USS, apply the icon styles in UXML.

#### Example (UXML)
```xml
<VisualElement class="icon-home" />
<VisualElement class="icon-settings" />
```
This applies the home and settings icons as backgrounds to `VisualElement` components.

<Note type="warning">
Ensure the icon paths in USS match the actual icon locations in your Unity project.
</Note>

## Best Practices for Custom Icons

- **Maintain consistency** in style, size, and spacing.
- **Ensure clarity** by using recognizable and distinguishable icons.
- **Optimize images** by compressing them for better performance.
- **Consider accessibility** by ensuring icons have good contrast.
- **Use interactive feedback**, such as hover effects.

#### Example (Adding Hover Effect)
```css
.icon-home:hover {
    opacity: 0.8;
}
```
This slightly reduces opacity when hovered, improving user feedback.

## Conclusion

Custom icons enhance UI usability and branding. By importing, defining, and applying icons in USS and UXML, you can create a clear and engaging interface. Following best practices ensures performance, accessibility, and consistency in your Unity UI.