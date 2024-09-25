# Payments

## Introduction

[Payments](/learn/studio/api/services/Payments) are a crucial part of many games and experiences, allowing players to purchase in-game items, unlock content, and support developers. In this guide, you'll learn how to implement payments in your Highrise Studio projects using the Highrise Payments API.

<Note type="warning">
World owner cannot purchase their own IWPs. You will need to use a different account to test the purchase flow in the app.
</Note>

## Setting Up Payments

### Step 1: Create In-World Purchases
1. Go to the [Creator Portal](https://create.highrise.game/)
2. Select the world you want to create a product for
3. Navigate to the **In-World Purchases** section under the **Monetization** tab
4. Click on the **Create** button
5. Fill in the product details, such as the product ID, name, description
6. Click on the **Create** button to create the product

<Note type="warning">
In-World Purchases (IWP) product ID is a unique string that identifies the product. It is used to reference the product in your scripts.
</Note>

<Note type="warning">
Highrise will take 30% of the revenue generated from the sale of In-World Purchases (IWP). The remaining 70% will be credited to your account.
</Note>

### Step 2: Creating a Payment Handler (Optional)
1. Right-click in the project panel and select `Create > Lua > Module`
2. Give your module a name, such as `PaymentHandlerScript`
3. Right-click in the Hierarchy panel and select `Create Empty`
4. Give the empty object a name, such as `PaymentHandler`
5. Drag the `PaymentHandlerScript` module onto the `PaymentHandler` object
6. Open the `PaymentHandlerScript` module and follow Step 3 below

### Step 3: Implementing the Payment Handler
<Note type="warning">
All payment-related scripts are done on the server side. Do not use payment-related functions on the client side.
</Note>

```lua
--!Type(Module)

--[[
  In this example we will be using "tokens" as the currency
  This is currently stored locally, but you should store it in Storage or Inventory for persistence
]]

-- Keep track of the players and their tokens
local tokens = 0 -- Please use Storage or Inventory instead (this is just an example)

-- Function to Prompt the player to purchase a token (Client Side)
function PromptTokenPurchase(id: string)
  Payments:PromptPurchase(id, function(paid)
    if paid then
      print("Purchase successful")
    else
      print("Purchase failed")
    end
  end)
end

-- Function to increment the player's tokens (Server Side)
function IncrementTokens(player: Player, amount: number)
  -- Note: Remember to add your own logic if you are using Network values or Storage
  -- In this case we are only storing the tokens locally (not recommended but for example purposes)
  tokens = tokens + amount

  -- Print the player's name, the amount of tokens they received, and their total tokens
  print(player.name .. " received " .. amount .. " tokens. Total tokens: " .. tokens)
end

-- Function to handle the purchase (Server Side)
function ServerHandlePurchase(purchase, player: Player)
  -- Note: The product ID is a string even when it represents a number
  local productId = purchase.product_id -- The product ID that was purchased (e.g., "token")

  -- The amount of tokens to give the player
  local tokensToGive = 0 -- Initialize the amount of tokens to give

  -- Assuming you have multiple products to purchase (e.g., "token_100", "token_500")
  if productId == "token_100" then
    tokensToGive = 100
  elseif productId == "token_500" then
    tokensToGive = 500
  else
    -- No product found, reject the purchase and return
    Payments.AcknowledgePurchase(purchase, false)
    -- Add an extra message to the console to help with debugging
    print("Unknown product ID: " .. productId)
    return
  end

  -- The purchase was successful, acknowledge the purchase and give the player the tokens
  Payments.AcknowledgePurchase(purchase, true, function(ackErr: PaymentsError)
    -- Check for any errors when acknowledging the purchase
    if ackErr ~= PaymentsError.None then
      print("Error acknowledging purchase: " .. ackErr)
      return
    end

    -- Add the tokens to the player's account (calling the IncrementTokens function)
    IncrementTokens(player, tokensToGive)
  end)
end

-- Initialize the module
function self:ServerAwake()
  -- IMPORTANT: Register the ServerHandlePurchase function as the callback for the PurchaseHandler
  Payments.PurchaseHandler = ServerHandlePurchase
end
```

### Step 4: Calling the Payment Handler
```lua
--!Type(UI)

-- Now assuming the module script is named PaymentHandlerScript
local PaymentHandler = require("PaymentHandlerScript")

-- Assuming you have a button called PurchaseButton
--!Bind
local PurchaseButton : UIButton = nil

-- Register the callback for the button press
PurchaseButton:RegisterPressCallback(function()
  -- Call the PromptTokenPurchase function when the button is clicked
  PaymentHandler.PromptTokenPurchase("token_100")
end, true, true, true)
```

### Step 5: Testing the Payment Handler

1. In the Unity Editor select `Highrise > World Settings`
2. Under the **World** tab, set the **World** to the world you created the product for
3. This will allow you to test the payment handler in the Unity Editor

<Note type="info">
The gold will not be deducted from your account when testing in the Unity Editor.
</Note>

## Summary of Functions

### Prompting the Player to Purchase
When you want to prompt the player to purchase an item, you can call the `PromptPurchase` function and pass the product
ID and a callback function.

```lua
-- Prompt the player to purchase a token
Payments.PromptPurchase("token_100", function(paid: boolean)
  if paid then
    print("Purchase successful")
  else
    print("Purchase failed")
  end
end)
```

### Handling the Purchase
When a player makes a purchase, you need to handle the purchase on the server side. You can call the `ServerHandlePurchase` function and pass the purchase object and the player object.

```lua
-- Handle the purchase
PaymentHandler.ServerHandlePurchase(purchase, player)
```

### Acknowledging Purchases
When a player makes a purchase, you need to acknowledge the purchase to complete the transaction. You can acknowledge a purchase by calling the `AcknowledgePurchase` function and passing the purchase object, a boolean value indicating whether the purchase was successful, and an optional callback function.

```lua
-- Acknowledge the purchase
Payments.AcknowledgePurchase(purchase, true, function(ackErr: PaymentsError)
  -- Check for any errors when acknowledging the purchase
  if ackErr ~= PaymentsError.None then
    print("Error acknowledging purchase: " .. ackErr)
    return
  end

  -- Add the tokens to the player's account (calling the IncrementTokens function)
  IncrementTokens(player, tokensToGive)
end)
```

### Rejecting Purchases

If the purchase fails or if the product ID is unknown, you can reject the purchase by calling the `AcknowledgePurchase` function and passing the purchase object and a boolean value indicating that the purchase failed.

```lua
-- Reject the purchase
Payments.AcknowledgePurchase(purchase, false)
```

## Conclusion

In this guide, you learned how to implement payments in your Highrise Studio projects using the Highrise Payments API. By following the examples provided, you can create In-World Purchases (IWP), handle purchases, and acknowledge or reject purchases in your project. Implementing payments in your project can help you monetize your game or experience and provide players with a way to support your work.