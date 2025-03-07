# UXML Nesting

## Introduction

Nesting UI elements correctly in **UXML** is essential for maintaining clarity, performance, and responsiveness. While nesting helps structure complex UIs, **over-nesting can lead to unnecessary complexity**.

This guide covers:
- When to use **nesting**
- When to **avoid over-nesting**
- How to **structure elements efficiently**
- Using **`flex-direction: row`** vs **`flex-direction: column`** for proper layout alignment

## When to Use Nesting

Nesting is useful when:
- Grouping related elements together for better organization.
- Creating containers that hold multiple elements.
- Structuring UI elements that should move together.

✔ **Good Example (Organized Structure)**
```xml
<VisualElement class="profile-card">
    <VisualElement class="profile-header">
        <Label class="username" text="Player123" />
    </VisualElement>

    <VisualElement class="profile-body">
        <Image class="profile-picture" />
        <Label class="player-status" text="Online" />
    </VisualElement>
</VisualElement>
```
### Why is this good?
- The **profile-header** groups related header elements.
- The **profile-body** contains profile details.
- Minimal nesting, making it easy to read and maintain.

## When to Avoid Over-Nesting

Too much nesting **complicates UI structure** and can cause **performance issues**.

❌ **Bad Example (Over-Nested Structure)**
```xml
<VisualElement>
    <VisualElement>
        <VisualElement>
            <VisualElement>
                <Label text="Too much nesting!" />
            </VisualElement>
        </VisualElement>
    </VisualElement>
</VisualElement>
```

✔ **Improved Example (Flattened Structure)**
```xml
<VisualElement class="message-box">
    <Label text="Well-structured UI" />
</VisualElement>
```
### Why is this better?
- Uses fewer unnecessary containers.
- Improves readability and performance.

## Using `flex-direction` for Nesting Layouts

The **`flex-direction`** property determines how nested elements are arranged horizontally (`row`) or vertically (`column`).

### `flex-direction: column` (Stack Elements Vertically)

✔ **Good Example (Vertical Layout)**
```xml
<VisualElement class="vertical-layout">
    <Label class="title" text="Profile Info" />
    <Image class="profile-picture" />
    <Label class="status" text="Online" />
</VisualElement>
```

**Corresponding USS:**
```css
.vertical-layout {
    flex-direction: column;
    align-items: center;
}
```
**Why use a column layout?**
- Aligns elements **vertically**.
- Ensures **consistent spacing**.

### `flex-direction: row` (Align Elements Horizontally)

✔ **Good Example (Horizontal Layout)**
```xml
<VisualElement class="horizontal-layout">
    <Image class="profile-picture" />
    <Label class="username" text="Player123" />
    <Label class="status" text="Online" />
</VisualElement>
```

**Corresponding USS:**
```css
.horizontal-layout {
  flex-direction: row;
  align-items: center;
}
```
**Why use a row layout?**
- Aligns elements **horizontally**.
- Ensures elements **stay in line**.

## Conclusion

- **Use nesting wisely** – Only when needed.
- **Avoid deep nesting** – Keep structures simple.
- **Use `flex-direction: row` or `column`** – Organize elements efficiently.

By following these guidelines, your **UXML layouts will remain structured, readable, and easy to maintain**.