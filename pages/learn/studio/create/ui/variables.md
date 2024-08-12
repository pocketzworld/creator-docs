# Variables

## Introduction

Variables in UI design are placeholders that store information or values that can be reused throughout your design. They allow you to define a value once and use it in multiple places, making it easier to maintain consistency and make global changes to your design.

In Highrise Studio, you can define custom variables in your UI stylesheet (USS) to store values such as colors, font sizes, spacing, and more. By using variables, you can create a centralized system for managing design properties and ensure that your UI elements are visually consistent.

## Creating Custom Variables

To create custom variables in your USS file, follow these steps:

### Step 1: Define a Variable

1. Open your USS file in a text editor or the Unity editor.
2. Define a variable using the `--` prefix followed by a name and assign a value to it.

   ```css
   :root {
       --primary-color: #3498db;
       --secondary-color: #2ecc71;
       --font-size: 16px;
   }
   ```

   - In the example above, we define three custom variables: `--primary-color`, `--secondary-color`, and `--font-size`. These variables store color values and font sizes that can be reused throughout the stylesheet.

### Step 2: Use the Custom Variables

Once you have defined your custom variables, you can use them in your stylesheet to apply the values to your UI elements.

1. Reference the custom variables in your CSS properties.

   ```css
   .button {
       background-color: var(--primary-color);
       color: white;
       font-size: var(--font-size);
   }
   ```

   - In this example, the `.button` class uses the `--primary-color` and `--font-size` variables to set the background color and font size of the button. By referencing the custom variables, you can easily update the values across your design by modifying the variables' definitions.

## Tips for Using Variables

While you can define custom variables for various design properties, here are some tips to help you effectively use variables in your UI design:

- **Consistency**: Store common values like colors and font sizes in variables to keep your design consistent.
- **Reusability**: Use variables for repeated values to reduce redundancy and simplify global updates.
- **Organization**: Group related variables in your stylesheet for better organization and management.
- **Naming**: Choose descriptive names for variables to clarify their purpose and make maintenance easier.
- **Updates**: Regularly review and adjust variables to ensure they meet your current design needs.

## Conclusion

Variables are key in UI design for creating reusable, consistent elements. Define custom variables in your USS file to streamline your design, maintain visual coherence, and simplify updates. Use them in Highrise Studio to enhance your workflow and create appealing interfaces.
