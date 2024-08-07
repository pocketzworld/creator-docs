# Using Custom Fonts in Unity UI

## Introduction
Enhance your Unity projects by incorporating custom fonts into your user interface. This guide will walk you through the process of importing a font and using it in your UI designs. For detailed information, you might want to reference Unity's documentation on USS (Unity Style Sheets) and UXML (Unity Extensible Markup Language).

## Step 1: Import Your Font

1. **Create a Fonts Directory**:
   - Organize your assets by creating a dedicated 'Fonts' directory within your Unity project. This helps in managing your assets cleanly and logically.

2. **Add the Font File**:
   - Drag and drop your font file (typically a `.ttf` file, though other formats are supported) into the 'Fonts' directory in your project window.

3. **Create a Font Asset**:
   - Click on your imported font file in the project window.
   - Right-click and select `Create > Text > Font Asset`. This action converts your font file into a usable `.asset` file, which Unity can handle more efficiently in the UI system. The new asset will appear in the same directory as the original font file.

## Step 2: Define Your Font in the Stylesheet

1. **Edit Your USS File**:
   - Open or create a USS file that styles the elements of your UI. This stylesheet controls the appearance of your UI elements, similar to CSS in web development.

2. **Set the Font**:
   - In your USS file, use the `-unity-font-definition` property to set the font. You need to specify the path to the `.asset` file you created from your original font file. Make sure to adjust the path according to your project's folder structure.

   ```css
   .simple-leaderboard {
       flex-grow: 1;
       background-image: url("project://database/Assets/TorePaper.png");
       -unity-font-definition: url("project://database/Assets/UI/Fonts/QuickPencil-Regular SDF.asset");
   }
   ```

   - In the example above, `.simple-leaderboard` is a class applied to a UI element in the UXML. The `flex-grow: 1` property allows the element to expand to fill its container, and the `background-image` sets a background texture. The crucial line for the font is the `-unity-font-definition`, which points to the `QuickPencil-Regular SDF.asset` file you created.


## Step 3: Custom Variables

After defining the font in your USS file, you can use custom variables to reference the font throughout your stylesheet. This approach allows you to reuse the font definition easily and maintain consistency across your UI elements.

1. **Define a Custom Variable**:
   - Create a custom variable in your USS file to represent the font definition. This variable can be referenced wherever you need to apply the font.

   ```css
   :root {
       --font-custom: url("project://database/Assets/UI/Fonts/QuickPencil-Regular SDF.asset");
   }
   ```

   - In this example, `--font-custom` is a custom variable that points to the font asset file. You can name your variable according to your font's style or purpose.

2. **Use the Custom Variable**:
   - To apply the custom font to an element, reference the custom variable in your stylesheet. This method simplifies font management and allows you to update the font across your UI by modifying a single variable.

   ```css
   .simple-leaderboard {
       flex-grow: 1;
       background-image: url("project://database/Assets/TorePaper.png");
       -unity-font-definition: var(--font-custom);
   }
   ```

   - By using `var(--font-custom)`, you are applying the font definition stored in the custom variable to the `.simple-leaderboard` element.
  
<Note type="info">
This works for any other property you want to reuse across your stylesheet. Custom variables provide a convenient way to manage and update your styles efficiently.
</Note>

## Conclusion

By following these steps, you can start using custom fonts in your Unity UI to give your games and applications a unique and polished look. Custom fonts can significantly enhance the aesthetic appeal and user experience of your project. Don't forget to experiment with different fonts and styles to see what works best for your UI design needs.