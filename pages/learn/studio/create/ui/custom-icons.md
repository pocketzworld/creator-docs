# Using Custom Icons in Unity UI

## Introduction
Icons are important visual elements in user interfaces that help users quickly identify and interact with different functions or features.

In Unity, you can use custom icons to enhance the visual appeal of your UI and create a unique look for your game. This guide will walk you through the process of importing custom icons and using them in your Unity UI designs.

## Importing Custom Icons

### Step 1: Prepare Your Icons
1. **Create or Download Icons**:
     - Design or download the icons you want to use in your UI. Icons are typically small, simple images that represent specific actions, objects, or concepts.

2. **Organize Your Icons**:
      - Create a dedicated folder in your Unity project to store your icons. This helps keep your project organized and makes it easier to manage your assets.

### Step 2: Import Icons into Unity

1. **Add Icons to Your Project**:
     - Drag and drop your icon images into the folder you created for storing icons in the Unity Editor.
  
2. **Set Import Settings**:
      - Select the imported icons in the Project window and adjust the import settings as needed. You can set properties like texture type, compression, and size to optimize the icons for your UI.

## Using Custom Icons in Unity UI

### Step 1: Import Icons into Your UI USS

1. **Edit Your USS File**:
     - Open or create a USS file that styles the elements of your UI. This stylesheet controls the appearance of your UI elements, similar to CSS in web development.
  
2. **Define Icon Classes**:
      - Define classes in your USS file that reference the custom icons you imported. You can use these classes to apply the icons to specific UI elements.

    ```css
    .icon-home {
        background-image: url("project://database/Assets/UI/Icons/home.png");
    }

    .icon-settings {
        background-image: url("project://database/Assets/UI/Icons/settings.png");
    }
    ```

    - In the example above, we define two classes, `.icon-home` and `.icon-settings`, that set the background images to the respective icon files.

<Note type="info">
You can use absolute or relative paths to reference your icon images in the USS file. Make sure the paths are correct based on your project's folder structure.
</Note>

### Step 2: Apply Icons to UI Elements

1. **Use Icon Classes in UXML**:
     - In your UXML files, apply the icon classes to the UI elements where you want to display the custom icons.

    ```xml
    <VisualElement class="icon-home" text="Home" />
    <VisualElement class="icon-settings" text="Settings" />
    ```

    - In this example, we apply the `.icon-home` class to a VisualElement element to display the "home" icon as its background image. Similarly, the `.icon-settings` class is applied to another VisualElement element to display the "settings" icon.

[Learn how to create variables in Unity UI](https://create.highrise.game/learn/studio/create/ui/variables)

## Tips for Using Custom Icons

- **Consistency**: Maintain a consistent style and size for your custom icons to create a cohesive UI design.
- **Clarity**: Ensure your icons are easily recognizable and convey their intended meaning clearly.
- **Optimization**: Optimize your icon images for performance by using appropriate compression settings and sizes.
- **Accessibility**: Consider accessibility when designing icons to ensure they are visible and understandable to all users.
- **Feedback**: Use icons to provide visual feedback on user actions, such as button presses or menu selections.

## Conclusion

Custom icons can add a personal touch to your Unity UI designs and improve the overall user experience. By importing and using custom icons in your projects, you can create visually appealing interfaces that engage and delight your players. Experiment with different icon styles and designs to find the perfect fit for your game's UI.