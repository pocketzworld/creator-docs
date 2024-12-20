# CheatCommandModule

The `CheatCommandModule.lua` is a critical tool designed to facilitate debugging and testing by providing a wide array of cheat commands. These commands allow developers and testers to manipulate game states, unlock features, and validate functionalities efficiently.

## Overview

The `CheatCommandModule` provides:

- **Command Parsing**: Processes player input to identify commands and arguments.
- **Player Validation**: Ensures only authorized players can execute commands.
- **Client-Server Communication**: Supports both client-side and server-side command execution.
- **Integration**: Links with game management modules to perform actions like unlocking quests, modifying contests, or resetting data.

## Key Components

### 1. **Command Processing**

#### Parsing Commands
Commands are parsed using the `ParseCommand` function, which identifies the command keyword and associated arguments.

##### Key Functions
- `SplitString(input)`: Splits a string into individual words.
- `ParseCommand(input)`: Extracts the command keyword and arguments from a player’s input.

#### Command Execution
Commands are executed if they exist in the `commands` table and the player has the necessary permissions.

##### Key Functions
- `CommandExists(command)`: Checks if a command is defined.
- `CanPlayerRunCommand(player)`: Validates if a player is authorized to execute commands.

### 2. **Player Validation**

#### Authorization Logic
Only players listed in `_validPlayers` or in test mode (`_testMode`) can run commands.

##### Key Logic
- `CanPlayerRunCommand(player)`: Returns true if the player is authorized based on `_validPlayers` or `_testMode`.

### 3. **Command Registry**

#### Registered Commands
The module defines a set of cheat commands in the `commands` table. These commands invoke corresponding functions from other game modules.

##### Available Commands
- `/help`: Displays a list of available commands.
- `/cleardata`: Resets all player data.
- `/addreward`: Grants rewards to the player.
- `/debugquests`: Enables quest debugging mode.
- `/deletecontests`: Clears all active contests.
- `/addcontestplayers`: Adds test players to a contest.
- `/addtickets`: Grants tickets for contests.
- `/setcontestvotes`: Adjusts votes for a contest.
- `/unlockcontest`: Unlocks a specific contest.
- `/completequests`: Completes specified quests.

### 4. **Client-Side Operations**

Handles player input and executes commands locally or sends them to the server for execution.

#### Key Functions
- **Command Execution**:
  - Captures and processes player input in chat.
  - Executes commands locally or triggers server requests.
- **Event Handling**:
  - `chatCommandRequest`: Sends commands to the server.
  - `chatCommandResponse`: Processes responses from the server.
- **Help Command**:
  - Displays all available commands to the player.

### 5. **Server-Side Operations**

Processes server-specific commands and broadcasts responses to all clients.

#### Key Functions
- `chatCommandRequest:Connect`: Handles incoming requests from clients.
- `chatCommandResponse:FireAllClients`: Sends responses to all connected clients.

## Workflow Examples

### Command Execution Workflow
1. **Player Input**:
   - Player enters a command in chat (e.g., `/addreward`).
2. **Parsing**:
   - `ParseCommand` extracts the command keyword and arguments.
3. **Validation**:
   - `CanPlayerRunCommand` checks if the player is authorized.
4. **Execution**:
   - The corresponding function from the `commands` table is invoked.
5. **Response**:
   - Success or error messages are displayed to the player.