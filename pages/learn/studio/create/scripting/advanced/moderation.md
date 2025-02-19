# Moderation API

## Introduction

This guide introduces you to the Highrise Moderation API, which allows for implementing moderation functionalities within your Highrise Studio projects. Using this API, developers can programmatically manage player behavior to maintain a positive gaming environment.

<Note type="warning">
The Highrise Moderation API is designed for server-side integration and should only be employed within server scripts.
</Note>


## Using the Highrise Moderation API

### Overview

The Highrise Moderation API provides methods to kick, ban, unban, mute, unmute, and fetch lists of banned players directly from your server scripts. Here are detailed examples and best practices for using these methods.

### API Method Examples

<Note type="info">
To operate these methods, you need to work with the player object directly, not just their ID.
</Note>

#### Kick a Player

```lua
function self:ServerAwake()
  -- Kick a player from the server
  Moderation.Kick(player, function(err: ModerationError)
    if err ~= ModerationError.None then
      print("Failed to kick player: " .. err)
    else
      print("Player kicked successfully")
    end
  end)
end
```

#### Ban a Player

<Note type="info">
Specify the ban duration in seconds.
</Note>

```lua
function self:ServerAwake()
  -- Ban a player from the server for a specific duration
  local duration = 3600 -- 1 hour
  Moderation.Ban(player, duration, "Reason for ban", function(err: ModerationError)
    if err ~= ModerationError.None then
      print("Failed to ban player: " .. err)
    else
      print("Player banned successfully")
    end
  end)
end
```

#### Unban a Player

<Note type="info">
Unbanning a player requires their unique player ID.
</Note>

```lua
function self:ServerAwake()
  -- Unban a player using their player ID
  Moderation.Unban(player_id, function(err: ModerationError)
    if err ~= ModerationError.None then
      print("Failed to unban player: " .. err)
    else
      print("Player unbanned successfully")
    end
  end)
end
```

#### Mute a Player

<Note type="info">
The mute duration should also be specified in seconds.
</Note>

```lua
function self:ServerAwake()
  -- Mute a player for a specified duration
  local duration = 3600 -- 1 hour
  Moderation.Mute(player, duration, function(err: ModerationError)
    if err ~= ModerationError.None then
      print("Failed to mute player: " .. err)
    else
      print("Player muted successfully")
    end
  end)
end
```

#### Unmute a Player

```lua
function self:ServerAwake()
  -- Unmute a player
  Moderation.Unmute(player, function(err: ModerationError)
    if err ~= ModerationError.None then
      print("Failed to unmute player: " .. err)
    else
      print("Player unmuted successfully")
    end
  end)
end
```

#### Retrieve Banned Players List

```lua
function self:ServerAwake()
  -- Retrieve a list of banned players with pagination
  local limit = 10 -- Maximum number of entries
  local cursorId = "" -- Cursor ID for pagination

  Moderation.GetBannedPlayers(limit, cursorId, function(players: table<Player>, cursorId: string, err: ModerationError)
    for _, player in ipairs(players) do
      print("Banned player: " .. player.name)
    end
  end)
end
```

### Common Errors

When utilizing the Moderation API, you might encounter several errors. Here are the most common ones:

- `ModerationError.None`: No error occurred.
- `ModerationError.Count`: Invalid count provided.
- `ModerationError.CursorInvalid`: Provided cursor is invalid.
- `ModerationError.CursorInvalidLimit`: Provided cursor limit is invalid.
- `ModerationError.InsufficientPermissions`: Insufficient permissions to perform the operation.
- `ModerationError.InternalError`: An internal error occurred.
- `ModerationError.InvalidUserId`: The provided user ID is invalid.
- `ModerationError.RequestThrottled`: The request has been throttled.
- `ModerationError.Timeout`: The request timed out.
- `ModerationError.UnknownError`: An unknown error occurred.

It's crucial to handle these errors in your server scripts to ensure robust moderation management.

## Conclusion

Leverage the Highrise Moderation API to seamlessly integrate moderation features within your games, ensuring a safe and engaging environment for all participants.