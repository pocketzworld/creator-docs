# Payments

## Introduction

[Payments](/learn/studio/api/services/Payments) are a crucial part of many games and experiences, allowing players to purchase in-game items, unlock content, and support developers. In this guide, you'll learn how to implement payments in your Highrise Studio projects using the Highrise Payments API.

### Payment API Example

Here's an example of how you can use the Highrise Payments API to handle purchases in your project:

<Note type="warning">
In the example below, we assume you have already set up a product. Look at the [Creating a Product](#creating-a-product) section to learn how to create a product.
</Note>

**Client Side:**
```lua
-- Assuming you have a players table to store the player's data, like tokens, etc.
local players = {}

-- Global function that can be called whenever you want to make a purchase
function PromptMakePurchase(player)
  if player ~= client.localPlayer then return end

  local product = "eel" -- The product ID you want to purchase
  Payments:PromptPurchase(product, function(paid)
    if paid then
      print("Purchase successful")
    else
      print("Purchase failed" .. tostring(paid))
    end
  end)
end
```

**Server Side:**
```lua
function self:ServerAwake()
  -- Register the PurchaseHandler function to be called when a purchase is made
  Payments.PurchaseHandler = ServerHandlePurchase
end

function ServerHandlePurchase(purchase, player: Player)
  local productId = purchase.product_id -- The product ID that was purchased

  -- Print the purchase information
  print("Purchase made by " .. player.name .. " for product " .. productId)

  local itemToGive = nil -- The item you want to give to the player
  if productId == "eel" then
    itemToGive = "item_eel"
  else
    -- Unknown product ID
    Payments.AcknowledgePurchase(purchase, false) -- Reject the purchase
    print("Unknown product ID: " .. productId)
    return
  end

  -- Give the item to the player, either by adding it to their inventory or saving it to their data
  -- In this example, we'll just print a message, and add tokens to the player's data
  print("Giving item " .. itemToGive .. " to " .. player.name)

  -- Add tokens to the player's data
  players[player].tokens = players[player].tokens + 100
end
```

**UI Script:**

Assuming you have a UI script that has a button that can be clicked to make a purchase, you can call the `PromptMakePurchase` function when the button is clicked.

<Note type="warning">
To call the `PromptMakePurchase` function, your script must be a module script, and you must require it in the UI script.
</Note>

```lua
--!Type(UI)

-- Now assuming the module script is named PurchaseHandler
local PurchaseHandler = require("PurchaseHandler")

-- Assuming you have a button called PurchaseButton
--!Bind
local PurchaseButton : UIButton = nil

-- Register the callback for the button press
PurchaseButton:RegisterPressCallback(function()
  -- Call the PromptMakePurchase function when the button is clicked
  PurchaseHandler.PromptMakePurchase(client.localPlayer)
end, true, true, true)
```

### Creating a Product

In order to use the Highrise Payments API, you need to create a product. You can create a product by following these steps:

1. Go to the **Creation** tab in the [Creator Portal](https://create.highrise.game/)
2. Select the world you want to create a product for
3. Navigate to the **World Products** section under the **Monetization** tab
4. Click on the **Create** button
5. Fill in the product details, such as the product ID, name, description.
6. Click on the **Create** button to create the product

Once you have created a product, you can set an image for the product, enable "List For Sale" to make it available for purchase, and set the price of the product.

<Note type="warning">
Highrise will take 30% of the revenue generated from the sale of products. The remaining 70% will be credited to your account.
</Note>

## Handling Purchases

When a player makes a purchase, the `ServerHandlePurchase` function is called on the server. This function is responsible for handling the purchase, giving the player the item they purchased, and acknowledging the purchase.

### Acknowledging a Purchase

After handling the purchase, you need to acknowledge the purchase to let the Highrise Payments API know that the purchase was successful. You can acknowledge a purchase by calling the `Payments.AcknowledgePurchase` function with the purchase object and a boolean value indicating whether the purchase was successful.

```lua
Payments.AcknowledgePurchase(purchase, true)
```

### Rejecting a Purchase

If the purchase cannot be completed for any reason, you can reject the purchase by calling the `Payments.AcknowledgePurchase` function with the purchase object and a boolean value indicating that the purchase failed.

```lua
Payments.AcknowledgePurchase(purchase, false)
```

## Conclusion

In this guide, you learned how to implement payments in your Highrise Studio projects using the Highrise Payments API. By following the examples provided, you can create products, handle purchases, and acknowledge or reject purchases in your project. Implementing payments in your project can help you monetize your game or experience and provide players with a way to support your work.