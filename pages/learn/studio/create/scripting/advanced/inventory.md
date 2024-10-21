# Inventory

## Introduction

Invntory is a great way to keep track of items that players have collected in your game. In this guide, you'll learn how to implement inventory in your Highrise Studio projects using the Highrise Inventory API.

### Inventory API Example

Here's an example of how you can use the Highrise Inventory API to handle inventory in your project:

<Note type="warning">
For the Inventory you don't need an actual IWP, you can just create a new table in the player's data to store the items.
</Note>

1. `InventoryTransaction.new()` - Creates a new inventory transaction.
2. `Inventory.CommitTransaction` - Commits the transaction to the player's inventory.
3. `Inventory.GetPlayerItems` - Retrieves the player's items.
4. `Inventory.GetPlayerItem` - Retrieves a specific item from the player's inventory.

**Giving an item to a player:**

Giving an item to a player will be handled by creating a new transaction and committing it to the player's inventory. It doesn't require any additional setup.

```lua
-- Create a new transaction and give the player a specified item
local transaction = InventoryTransaction.new():GivePlayer(player, itemId, amount)
-- Commit the transaction to apply the changes
Inventory.CommitTransaction(transaction)

-- Optionally, retrieve all of the player's items after the transaction is completed
Inventory.GetPlayerItems(player, limit, cursorId, function(items, newCursorId, errorCode)
    -- Your logic for handling the retrieved items goes here
end)
```

**Taking an item from a player:**

```lua
-- Create a new transaction and take a specified item from the player
local transaction = InventoryTransaction.new():TakePlayer(player, itemId, amount)
-- Commit the transaction to apply the changes
Inventory.CommitTransaction(transaction)

-- As above, you can also retrieve the player's items if needed
```

**Giving and taking items simultaneously:**

```lua
-- Create a transaction that takes currency and gives an item to the player
local transaction = InventoryTransaction.new()
    :TakePlayer(player, "YOUR_PRODUCT", PRICE_NUMBER)  -- Deduct the currency
    :GivePlayer(player, "YOUR_PRODUCT", AMOUNT_NUMBER) -- Add the purchased item

-- Commit the transaction to apply the changes
Inventory.CommitTransaction(transaction)
```

**Retrieving a player's item:**

```lua
-- Retrieve a specific item from the player's inventory
Inventory.GetPlayerItem(player, itemId, function(item)
    -- Your logic for handling the retrieved item goes here
end)
```

<Note type="warning">
Inventory only stores the "itemId" and "amount" of the item. To add more information about the item, you can create a separate table to store the item's data.
</Note>

### Error Handling
You can also enhance your transactions by checking for errors, which are listed [here](https://create.highrise.game/learn/studio-api/api/classes/InventoryError). This is particularly useful if your server has high traffic and you encounter errors like throttling.

### Additional Tips
Consider creating a separate module script just for handling inventory functions. This way, you can easily call these functions from anywhere in your code.

## Conclusion

Use the Highrise Inventory API to manage the items that players collect in your game, and create a more engaging experience for your players.