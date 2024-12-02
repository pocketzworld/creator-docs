# Deep Links in Highrise Studio

## Introduction
Deep links provide a convenient way to navigate directly to specific pages or UI elements within Highrise Studio. These links can be used to streamline user navigation, such as displaying an **Items Popup**, opening the **Closet**, or directing users to a specific **World Rating** page.

## Deep Link Format
Deep links in Highrise always follow this structure:  
```
https://high.rs/<path>?<parameters>
```

### Example
To navigate to an **Items Popup** for a specific item, use:  
```
https://high.rs/item?id=<item_id>
```
For instance, to display the item with ID `1231284`:  
```
https://high.rs/item?id=1231284
```

<Note type="warning">
The exact format of the deep link may vary depending on the destination page or UI element.
</Note>

## Deep Links vs. URL Parameters
While both deep links and URL parameters pass information, their purposes differ:
- **Deep Links**: Navigate to or display specific UI elements within Highrise Studio.
- **URL Parameters**: Provide additional data or context to web pages.

## How to Use Deep Links

### Method 1: Using a UI Button
Call the `UI:ExecuteDeepLink` method, passing the deep link as an argument:
```lua
UI:ExecuteDeepLink("https://high.rs/world?id=66fdaea5ea835d1b69eb608b&rate=true")
```

### Method 2: Using a Component
1. Create an **Empty GameObject** in your scene.
2. In the **Inspector** panel, click `Add Component` and add:
   - **Tap Handler** (Script)
   - **Deep Link Executor** (Script)
   - **Box Collider** (Component)
3. In the **Deep Link Executor** component, input the desired deep link.
4. Optional: Uncheck "Check Distance" in the **Tap Handler** component to disable distance-based interaction.

## Deep Link Examples

### Items Popup
To open the **Items Popup**, use this format:  
```
https://high.rs/item?id=<item_id>&type=<item_type>
```

You can find the `item_id` on the [Highrise Marketplace](https://highrise.game/catalog?type=clothing&page=1). Item links follow this format: `https://highrise.game/catalog/item/563a8fab614698c51b000026`, where `563a8fab614698c51b000026` is the `item_id`.

#### Parameters
- `item_id`: The unique ID of the item.  
- `item_type`: The type of item, which can be:
  - `avatar_item`
  - `collectible`
  - `furniture`
  - `gacha_tokens`
  - `gems`
  - `lucky_tokens`
  - `pops`
  - `_` (for unknown item types)

#### Example
To display an item with ID `1231284` and type `avatar_item`:  
```
https://high.rs/item?id=1231284&type=avatar_item
```

## Conclusion
Deep links are a powerful feature in Highrise Studio, allowing developers to create direct navigation paths to specific content or UI elements. Whether you're enhancing user experience by simplifying access to key features or creating dynamic interactions, deep links are an essential tool for Studio development.