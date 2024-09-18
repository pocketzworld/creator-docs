# Matchmaking

## Introduction

The priority of in which room players will be placed is determined by the matchmaking system. In this guide, you'll learn how to implement matchmaking in your Highrise Studio projects using the Highrise Matchmaking API.

### Matchmaking API Example

Here's an example of how you can use the Highrise Matchmaking API to handle matchmaking in your project:

<Note type="warning">
Matchmaking will be ignored if there's only 1 instance that can be joined.
</Note>

```lua
function self:ServerAwake()
  -- Set the matchmaking priority to 0.5
  -- This instance will be preferred over instances with a lower priority
  -- Not over instances with a higher priority
  server.SetMatchMakingPriority(0.5)

  -- Set the matchmaking priority to 0
  -- This instance will be ignored by the matchmaking system
  -- Players can still join this instance directly
  server.SetMatchMakingPriority(0)

  -- Retrieve the matchmaking priority of this instance
  local priority = server.GetMatchMakingPriority()
  print("Matchmaking priority: " .. priority) -- 0
end
```

### Matchmaking Usage

Let's say you have a world that has a round-based game mode like a "tic-tac-toe" game. You can set the matchmaking priority to 0 when the game starts and this will prevent players from joining the game in the middle of a round, instead they will be placed in a new instance.

Once the game ends, you can set the matchmaking priority to anything above 0, and players will be placed in the instance with the highest priority.

Priority can be calculated based on the number of players in the instance, the current round, or any other criteria you want to use.

<Note type="info">
The matchmaking priority is a float value between 0 and 1. The higher the value, the higher the priority.
</Note>

## Conclusion

Use the Highrise Matchmaking API to control the priority of instances in your game, and ensure that players are placed in the right instance at the right time.