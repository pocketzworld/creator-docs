# Store Mechanics Document

This document provides a detailed overview of the store mechanics implemented in the game, explaining how items are displayed, purchased, and managed.

## Overview

The store system allows players to purchase items such as clothing, rewards, and other in-game assets. It integrates with the inventory and currency systems to ensure seamless transactions and player engagement.

Key features include:
- Displaying store items with detailed information.
- Currency-based purchasing with validation.
- UI for browsing, selecting, and buying items.
- Reward delivery for purchased items.

## Core Concepts

### 1. **Store Item Templates**

Store item templates define the attributes and costs of items available for purchase.

#### Attributes
- **ID** (`_id`): Unique identifier for the store item.
- **Display Data** (`_displayData`): Visual representation, including name and image.
- **Cost** (`_cost`): Price of the item in the specified currency.
- **Currency Cost Template** (`_currencyCostTemplate`): Defines the type of currency required.
- **Reward Template** (`_clothingCollectionRewardTemplate`): Specifies the rewards for purchasing the item.

#### Key Functions
- `GetId`: Retrieves the item ID.
- `GetCost`: Returns the cost of the item.
- `GetCurrencyCostTemplate`: Retrieves the currency type.

### 2. **Item Store**

The `ItemStore.lua` module manages the logic for purchasing items and validating transactions.

#### Responsibilities
- Handling player purchase requests.
- Validating player ownership and currency.
- Deducting currency and awarding items.
- Saving updated player data.

#### Key Functions
- `RequestPurchaseItem`: Sends a purchase request to the server.
- `OnPurchaseItemRequest`: Handles server-side purchase validation.
- `OnPurchaseItemResponse`: Processes the server's response to a purchase.

#### Error Codes
- **None (0)**: No error.
- **NotEnoughCurrency (1)**: Insufficient currency.
- **AlreadyOwned (2)**: Player already owns the item.
- **ItemNotFound (3)**: Item does not exist.
- **UnknownError (4)**: An unexpected error occurred.

### 3. **UI Item Store**

The `UIItemStore.lua` script manages the visual and interactive aspects of the store.

#### Responsibilities
- Displaying available items and their details.
- Handling item selection and purchase confirmation.
- Updating the UI with player currency and ownership status.

#### Key Functions
- `Refresh`: Updates the store UI with current items and player currency.
- `CreateStoreEntry`: Creates UI elements for individual store items.
- `OnClickedItem`: Handles the purchase confirmation dialog.
- `OnPurchasedItem`: Displays rewards and refreshes the store after purchase.

## Workflow

1. **Opening the Store**
   - Triggered by interacting with an NPC or UI element.
   - The store UI is initialized with available items and player data.

2. **Browsing Items**
   - Players can view item details, including name, cost, and icon.
   - Owned items are marked, and unavailable items are greyed out.

3. **Purchasing an Item**
   - Players select an item and confirm the purchase in a dialog.
   - A server request validates the transaction.

4. **Delivering Rewards**
   - Upon successful purchase, rewards are delivered to the player’s inventory.
   - The UI updates to reflect the new ownership and currency balance.

## Example Implementation

### Example Store Item Template
```lua
local storeItemTemplate = {
  _id = "item_001",
  _displayData = displayTemplate,
  _cost = 100,
  _currencyCostTemplate = currencyTemplate,
  _clothingCollectionRewardTemplate = rewardTemplate,
}
```

### Requesting a Purchase
```lua
ItemStore.RequestPurchaseItem("item_001", function(response)
  if response.Success then
    print("Purchase successful!")
  else
    print("Purchase failed with error code:", response.Code)
  end
end)
```

## Key Events

### `OnPurchaseItemRequest`
Triggered when a player requests to purchase an item.

### `OnPurchaseItemResponse`
Handles the server’s response to a purchase request.

### `OnClickedItem`
Handles the player’s interaction with a store item.

### `Refresh`
Updates the store UI with current data.