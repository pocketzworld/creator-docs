# Responsive UI

## Introduction

In this guide, you will learn how to create a responsive user interface (UI) for your game. A responsive UI adapts to different screen sizes and orientations, ensuring that your game looks great on all devices.

<Note type="warning">
Assuming you have a basic understanding of UI design and development, this guide will focus on creating a responsive UI in Highrise Studio.
</Note>

## Designing a Responsive Container

To create a responsive UI, you need to design a container that adapts to different screen sizes.

```xml
<hr:UILuaView class="example">
  <VisualElement class="container">
    <!-- Add UI elements here -->
  </VisualElement>
</hr:UILuaView>
```

Now in your **USS** file, you can define the container's style properties.

```css
.example {
  display: flex; /* Use flexbox layout */
  
  align-self: center; /* Center horizontally */
  justify-content: center; /* Center vertically */
  align-items: center; /* Center items horizontally */

  width: 100%; /* Full width */
  height: 100%; /* Full height */
}

.container {
  display: flex; /* Use flexbox layout */
  flex-wrap: wrap; /* Wrap items */

  min-height: 450px; /* Minimum height */
  min-width: 350px; /* Minimum width */

  max-height: 660px; /* Maximum height */
  max-width: 800px; /* Maximum width */
}
```

The `example` class has a `display` property set to `flex`, which enables the use of flexbox layout. The `width` and `height` properties are set to `100%`, ensuring that the container takes up the full width and height of the screen.

The `min-height`, `min-width` properties define the minimum dimensions of the container and usually correspond to the smallest screen size you want to support. The `max-height`, `max-width` properties define the maximum dimensions of the container and usually correspond to the largest screen size you want to support.

`flex-wrap` allows the container to wrap its items when they exceed the available space, ensuring that they remain visible on smaller screens.

## Creating Responsive Text

```xml
<hr:UILuaView class="example">
  <VisualElement class="container">
    <VisualElement class="description">
      <hr:UILabel class="text" name="_descText" />
    </VisualElement>
  </VisualElement>
</hr:UILuaView>
```

<Note type="warning">
We will only focus on styling the text element in this example. The "example" class and the container styles are the same as the previous example.
</Note>

```css
.description {
  width: 100%; /* Full width */
  height: 100%; /* Full height */

  padding: 20px; /* Add padding */
  font-size: 16px; /* Set font size */

  -unity-text-align: middle-center; /* Center text */
  flex-wrap: wrap; /* Wrap text */
  white-space: normal; /* Allow text to wrap */

  flex-grow: 1; /* Grow to fill available space */
}

/** This is the important part **/
.text {
  white-space: normal; /* Allow text to wrap */
}
```

The `description` class has a `font-size` property set to `16px`, which defines the size of the text. The `white-space` property is set to `normal`, allowing the text to wrap when it reaches the edge of the container.

The `flex-grow` property is set to `1`, which allows the text to grow to fill the available space within the container.

The `text` class has the `white-space` property set to `normal`, ensuring that the text wraps correctly within the container.

## Additional Resources

To get a better understanding of UI design and development, we suggest you check out [USS Properties](https://docs.unity3d.com/Manual/UIE-USS-Properties-Reference.html) that can help you style your UI elements effectively.

## Conclusion

By following these steps, you can create a responsive UI for your game that adapts to different screen sizes and orientations. This will help ensure that your game looks great on all devices, providing a better user experience for your players.


