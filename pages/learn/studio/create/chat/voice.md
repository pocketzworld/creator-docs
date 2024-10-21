# Managing Voice Channels

## Introduction

Highrise offers a Voice API designed to enhance voice communications within your virtual world. This API enables you to establish distinct voice channels for various player groups, ensuring organized and efficient communication.

## Understanding Voice Channels

Voice channels facilitate real-time communication among players. You can create multiple channels tailored to specific player locations or roles, enhancing the overall user experience.

<Note type="warning">
By default, the world prefab includes a GeneralChat module, which generates an "All" channel with both voice and text functionalities enabled. Every player is automatically added to this channel.
</Note>

To create a voice channel, you need to specify its name, whether it allows text, voice, and its priority level.

```lua
local noSpeakingChannel = nil -- Channel reference

function self:ServerStart()
  -- Create a channel where players cannot speak
	noSpeakingChannel = Chat:CreateChannel("No Speaking", true, true, 1)
  -- Add a filter to control speaking permissions
	noSpeakingChannel.speakerFilter = restrictSpeaking -- Filter function

  -- Automatically add players to the channel upon connection
	server.PlayerConnected:Connect(function(player)
		Chat:AddPlayerToChannel(noSpeakingChannel, player)
	end)
end

-- Filter function to prevent players from speaking in the channel
function restrictSpeaking(player)
	return false
end
```

In this example, we establish a "No Speaking" channel where speaking is disabled by default.

## Customizing Player Channel Access

To allow players to switch between channels, add them to all the channels they should access. The first channel with voice enabled that they join will become their active voice channel. If a player is removed from or if their active channel is deleted, the channel with the highest priority they are in will become their new active channel. This also applies to text-enabled channels for text chat.

## Understanding Channel Priority

Channel priority determines a player's active channel when they are added to multiple channels. The channel with the highest priority will be the player's active channel.

```lua
Chat:CreateChannel("Channel 1", true, true, 1) -- Priority 1
Chat:CreateChannel("Channel 2", true, true, 2) -- Priority 2
```

<Note type="info">
It's acceptable to have multiple channels with the same priority. Setting a priority is optional when creating a channel.
</Note>

## Setting Channel Names

The channel name appears in the user interface. Ensure the names are unique to avoid confusion.

```lua
Chat:CreateChannel("My Team", true, true, 1) -- "My Team"
Chat:CreateChannel("Enemy Team", true, true, 1) -- "Enemy Team"
```

<Note type="info">
Channel names can include spaces. Channels will still appear in the UI even if they are empty.
</Note>

## Controlling Speaker Permissions

The `ChannelInfo.speakerFilter` allows you to define a function that determines if a player can speak in the channel. If this filter is not set, all players will be able to speak by default.

```lua
function restrictSpeaking(player)
	return false
end

noSpeakingChannel.speakerFilter = restrictSpeaking
```

<Note type="info">
You can apply the `speakerFilter` to a text-only channel to control who can text chat within it.
</Note>

## Conclusion

The Highrise Voice API empowers you to create and manage custom voice channels and speaker permissions, fostering a more engaging and immersive environment for players. For additional details on the Chat Service API, refer to the [Highrise Chat Service API documentation](https://create.highrise.game/learn/studio-api/services/Chat)