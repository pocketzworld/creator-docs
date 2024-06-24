# Controlling Voice Communications

## Introduction

Highrise provides a Voice API that allows you to control voice communications in your world. With the Voice API, you can create separate voice channels for different groups of players.

## Voice Channels

Voice channels allow players to communicate with each other in real-time. You can create multiple voice channels in your world to allow players to communicate with each other based on their location or role.

<Note type="warning">
By default the world prefab has a module named GeneralChat that creates a channel named "All" with voice and text enabled and adds each player into it
</Note>

You can create a voice channel by defining a channel name, allow text, allow voice, and priority.

```lua
local noSpeaking = nil -- Channel reference

function self:ServerStart()
  -- Create a channel with no speaking
	noSpeaking = Chat:CreateChannel("No Speaking", true, true, 1)
  -- Add a filter to the channel
	noSpeaking.speakerFilter = SpeakerOff -- Filter function

  -- Add player to the channel when they connect
	server.PlayerConnected:Connect(function(player)
		Chat:AddPlayerToChannel(noSpeaking, player)
	end)
end

-- function to filter players that can speak in the channel
function SpeakerOff(player)
	return false
end
```

In the example above, we create a channel named "No Speaking" where players are not allowed to speak by default.

## Customizing Chat Channels

If you want to allow players to change between channels, add the player to each of the channels they should have access to. The first channel with voice enabled they are added to will become their 'active channel,' meaning that is the one they will voice chat in. If the player is removed from the active channel or that channel is deleted, the channel they are in with the highest priority will become their new active channel. If the active channel also has text enabled, this will be the channel they will text chat in. If it does not have text enabled, then the text enabled channel with the highest priority will be the channel they will text chat in.

## Managing Speaker Permissions

The `ChannelInfo.speakerFilter` allows you to define a function that takes a player as an argument and returns true if the player should be able to speak and false if they should not be able to speak. If `speakerFilter` is not set, then everyone will be able to speak by default.

## Conclusion

The Voice API in Highrise allows you to create custom voice channels and manage speaker permissions. By using the Voice API, you can create more engaging and immersive experiences for your players. For more information on the Chat Service API, refer to the [Highrise Chat Service API documentation](https://create.highrise.game/learn/studio/api/services/Chat)