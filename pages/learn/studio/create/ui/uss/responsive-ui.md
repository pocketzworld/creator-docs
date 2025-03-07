# Responsive UI

## Introduction

A responsive UI adapts to different screen sizes and orientations, ensuring that your game looks great on all devices. By designing flexible UI layouts, you can provide a consistent user experience across various screen resolutions.

<Note type="warning">
This guide assumes a basic understanding of UI design and focuses on creating a responsive UI in Highrise Studio.
</Note>

## Key Considerations for Responsive UI

When designing a responsive UI, consider the following:

1. **UI elements should scale based on screen width and height.**  
   - Instead of fixed dimensions, use percentage-based widths and heights where possible.
   
2. **Containers help maintain structure.**  
   - Wrapping UI elements inside a container makes it easier to manage scaling.

3. **Use min/max dimensions for adaptability.**  
   - Setting minimum and maximum width and height prevents elements from becoming too small or too large.

4. **Flexbox and `flex-wrap` improve layout responsiveness.**  
   - Using `display: flex` allows elements to align and scale dynamically.

## Designing a Responsive Container

A well-structured UI starts with a responsive container.

### Example (UXML)
```xml
<hr:UILuaView class="example">
  <VisualElement class="container">
    <!-- Add UI elements here -->
  </VisualElement>
</hr:UILuaView>
```

### Example (USS)
```css
.example {
  display: flex; 
  align-self: center;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}

.container {
  display: flex;
  flex-wrap: wrap;
  min-height: 450px;
  min-width: 350px;
  max-height: 660px;
  max-width: 800px;
}
```
- The `.example` class ensures the container takes up the full screen.  
- The `.container` class defines minimum and maximum dimensions for scaling.  
- `flex-wrap: wrap;` allows elements to adjust when space is limited.

## Making UI Components Responsive

### Example: A Resizable View

A good practice is to define a **container inside the main UI component**. Below is an example for a **player list** that adapts to different screen sizes.

### Example (UXML)
```xml
<hr:UILuaView class="playerlist">
  <VisualElement class="container">
    <!-- Content here -->
  </VisualElement>
</hr:UILuaView>
```

### Example (USS)
```css
.playerlist {
  width: 100%;
  height: 100%;
  padding: 10px; /* Space around the container */
}

.container {
  display: flex;
  min-height: 300px;
  min-width: 350px;
  max-height: 600px;
  max-width: 600px;
}
```
- The `.playerlist` class ensures full-screen coverage with padding.
- The `.container` class restricts the scaling range to maintain usability.

If the screen size changes, the container **scales dynamically** while respecting its min/max limits.

## Creating Responsive Text

Ensuring text remains readable on all screen sizes is crucial.

### Example (UXML)
```xml
<hr:UILuaView class="example">
  <VisualElement class="container">
    <VisualElement class="description">
      <hr:UILabel class="text" name="_descText" />
    </VisualElement>
  </VisualElement>
</hr:UILuaView>
```

### Example (USS)
```css
.description {
  width: 100%;
  height: 100%;
  padding: 20px;
  font-size: 16px;
  -unity-text-align: middle-center;
  flex-wrap: wrap;
  flex-grow: 1;
}

.text {
  white-space: normal; /* Ensures text wraps */
}
```
- `flex-grow: 1;` allows the text container to expand when needed.
- `white-space: normal;` ensures text wraps instead of overflowing.

## Handling Responsive Grids and Scrollable Content

For layouts that include multiple items (e.g., **grids**), consider using **`flex-wrap` and `UIScrollView`**.

### Example (UXML)
```xml
<VisualElement class="grid-container">
  <hr:UIScrollView class="scrollable-content">
    <VisualElement class="grid-item" />
    <VisualElement class="grid-item" />
    <VisualElement class="grid-item" />
  </hr:UIScrollView>
</VisualElement>
```

### Example (USS)
```css
.grid-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  width: 100%;
  height: auto;
}

.scrollable-content {
  height: 400px;
  overflow: scroll;
}

.grid-item {
  width: 30%;
  height: 100px;
  margin: 5px;
}
```
- `flex-wrap: wrap;` ensures grid items adjust based on available space.
- `UIScrollView` enables scrolling when content exceeds the available height.

## Best Practices for Responsive UI

- Use **flexbox** (`display: flex`) to make layouts adaptable.
- Use **percentage-based** widths and heights when possible.
- **Min/max width and height** prevent elements from becoming too large or small.
- Use **`flex-wrap: wrap`** to allow elements to adjust dynamically.
- Use **scroll views** (`UIScrollView`) for large content that may exceed available space.

## Conclusion

By following these practices, you can create a responsive UI that adapts across different devices and screen sizes.  
Scaling elements dynamically, structuring UI with containers, and utilizing flexbox ensures that your UI remains clean and user-friendly.

For further customization, check out the [USS Properties Reference](https://docs.unity3d.com/Manual/UIE-USS-Properties-Reference.html).