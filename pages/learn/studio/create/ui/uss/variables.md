# USS Variables

## Introduction

Variables in UI design store reusable values, making it easier to maintain consistency and scalability. Instead of defining colors, font sizes, or spacing multiple times, you can declare them once and use them throughout your styles.

In Highrise Studio, you can define custom variables in USS (Unity Style Sheets) and even import predefined variables from the Highrise Studio package.

## Creating Custom Variables

### Step 1: Define Variables

Variables in USS use the `--` prefix and are typically declared inside `:root` for global usage.

#### Example (Defining Variables in USS)
```css
:root {
    --primary-color: #3498db;
    --secondary-color: #2ecc71;
    --font-size: 16px;
    --spacing-medium: 12px;
}
```
Why use variables?
- Changing `--primary-color` in one place updates all elements that use it.

### Step 2: Use Variables in Styles

Once defined, variables can be applied using `var(--variable-name)`.

#### Example (Using Variables in USS)
```css
.button {
    background-color: var(--primary-color);
    color: white;
    font-size: var(--font-size);
    padding: var(--spacing-medium);
}
```
Now, updating `--primary-color` automatically changes all buttons that use it.

## Importing Highrise Studio Variables

Instead of manually defining every variable, you can import predefined variables from Highrise Studio.

#### Example (Using Imported Variables in USS)
```css
var(--image-icon-close);
```
This imports `--image-icon-close` from the Highrise Studio package. You can find additional predefined variables inside the package files.

## Best Practices for Using Variables

- **Use a consistent naming convention**  
  Example:  
  - `--color-primary`  
  - `--font-heading`  
  - `--spacing-small`  

- **Group related variables together**  
  Keep colors, spacing, and typography separately organized.

- **Use variables for all repeated values**  
  Instead of hardcoding the same values multiple times, define once and reuse.

- **Review and update variables regularly**  
  As your UI evolves, keep your variables up to date.

## Conclusion

- Variables improve maintainability by allowing changes in one place.  
- Use `var(--variable-name)` to apply variables in USS.  
- Import Highrise Studio variables to maintain standard UI styles.  
- Keep variables structured and organized for better scalability.

By following these practices, you’ll create more flexible, reusable, and scalable UI designs in Highrise Studio.