# Transferring Gold to Players

## Introduction

In this guide, we will explore the process of transferring Gold to players in Worlds using the [World Wallet](https://create.highrise.game/learn/studio/distribute/monetization/world-wallet).

<Note type="warning">
Using the World Wallet functionality means you will be sending real Gold to your users. This can motivate malicious attempts to hack and exploit your world in order to acquire the Gold.

Ensure you fully understand and implement proper security measures for your World before integrating the World Wallet APIs. Refer to the following guide for initial steps on secure development: [Security Best Practices](https://create.highrise.game/learn/studio/create/scripting/lua/best-practices/security)
</Note>

## Transferring Gold

To transfer Gold to players in your World, you can use the `Wallet` API in Lua scripts. This API allows you to send Gold from the World Wallet to a player's account.

<Note type="warning">
This method will only work on the server-side Lua scripts. Do not expose this functionality to the client-side scripts to prevent cheating and unauthorized Gold transfers.
</Note>

Here is an example Lua script that transfers Gold to a player:

```lua
function TransferGold(player, amount)
  Wallet.TransferGoldToPlayer(player, amount, function(response, err)
    if err ~= WalletError.None then
			error("Something went wrong while transferring gold: " .. WalletError[err])
			return
		end

    print("Sent 1 Gold, Gold remaining: : ", response.gold)
  end)
end

-- Example usage
TransferGold(player, 10) -- Transfer 10 Gold to the player
```

## Getting World Wallet Balance

<Note type="info">
Each time you enter play mode in Unity, you start with 1,000 Gold in the world wallet to test the Gold transfer functionality.
</Note>

You can also retrieve the current balance of the World Wallet using the `Wallet` API. This allows you to monitor the Gold available in the World Wallet and manage transfers accordingly.

Here is an example Lua script that retrieves the World Wallet balance:

```lua
function GetWorldWalletBalance()
  Wallet.GetWallet(function(response, err)
		if err ~= WalletError.None then
			error("Something went wrong while retrieving wallet: " .. WalletError[err])
			return
		end

		print("Current Gold: ", response.gold)
	end)
end
```

## Error Codes

When transferring Gold to players, you may encounter various error codes that indicate the status of the transaction. Here are some common error codes you may encounter:

- `WalletError.None`: No error occurred during the transaction.
- `WalletError.InternalError`: An internal error occurred during the transaction.
- `WalletError.RequestThrottled`: The request was throttled due to rate limiting.
- `WalletError.UserNotFound`: The specified user was not found in the system.
- `WalletError.InsufficientResources`: The World Wallet does not have enough Gold to complete the transaction.

## Additional Considerations

<Note type="info">
Regular gold will be deducted from the World Wallet when transferring gold to players. If the balance is zero or insufficient, earned gold will be used instead.
</Note>

When transferring Gold to players, consider the following best practices:

- **Maximum Award Limit**: Set a maximum limit on the amount of Gold that can be transferred to a player in a single transaction to prevent abuse.
- **Minimum Balance Alert**: If your Gold balance reaches this amount, a notification will be sent in Highrise.

Learn more about managing your World Wallet in the [World Wallet guide](https://create.highrise.game/learn/studio/distribute/monetization/world-wallet).

## Conclusion

By leveraging the World Wallet APIs and Lua scripting, creators can reward players with Gold in their Worlds, enhancing the gameplay experience and fostering engagement. Implementing secure and efficient Gold transfers is essential to maintain the integrity of your World and protect player data. Stay informed, stay secure, and create immersive experiences with Highrise Studio.