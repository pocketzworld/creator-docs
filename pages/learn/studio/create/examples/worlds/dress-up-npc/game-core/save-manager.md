# SaveManager Module

The `SaveManager.lua` module serves as the backbone for handling player and global data in the game. It ensures that player progress, rewards, and other crucial game elements are persistently stored and synchronized between the client and server.

## Overview

The `SaveManager` module provides:

- **Player Data Management**: Saving and loading individual player data.
- **Global Data Management**: Handling shared game-wide data.
- **Event-Driven Communication**: Facilitating interactions between the client and server for data synchronization.
- **Support for Game Systems**: Integrating with quests, rewards, dress-up tasks, and currency.

## Key Components

### 1. **Player Data Structure**

Defines the data structure for tracking player-specific progress and achievements.

#### Attributes
- **PlayerId**: Unique identifier for the player.
- **SeenIntro**: Tracks if the player has viewed the intro.
- **CompletedTasks**: A list of task IDs the player has completed.
- **RewardList**: Stores earned rewards with their respective amounts.
- **QuestList**: Tracks quests the player is engaged in, along with progress.
- **ItemsPurchased**: A record of items purchased by the player.
- **RepeatCount**: The number of times the player has restarted certain tasks.

#### Functions
- `CreateNewPlayerSaveData(player)`: Initializes a new player data structure.
- `Validate(playerData)`: Ensures all player data fields are initialized and valid.

### 2. **Server-Side Data Management**

Handles saving, loading, and validating player data on the server.

#### Key Functions
- **Loading Data**:
  - `ServerLoadPlayerData(player)`: Retrieves data from storage or creates new data if none exists.
  - `LoadDataForPlayer(player, key, callback)`: Loads specific data for a player using a provided callback.
- **Saving Data**:
  - `ServerSavePlayerData(player, playerData, callback, sendClientResponse)`: Saves player data to storage.
  - `SaveDataForPlayer(player, key, data)`: Stores specific data for a player.
- **Global Data**:
  - `LoadGlobalData(key, callback)`: Retrieves global data.
  - `SaveGlobalData(key, data)`: Stores global data.
  - `UpdateGlobalData(key, validator, callback)`: Updates global data with a validator function.

### 3. **Client-Side Data Management**

Facilitates data synchronization and interaction for players on the client side.

#### Key Functions
- **Loading Data**:
  - `LoadPlayerData(OnLoaded)`: Requests and processes player data from the server.
  - `OnDataLoaded(playerData)`: Handles the response for loaded data.
- **Saving Data**:
  - `SavePlayerData()`: Sends updated player data to the server.
  - `ClearData()`: Resets player data to default values and saves.
- **Dress-Up Integration**:
  - `CompleteDressUpRequest(id, callback)`: Requests completion of a dress-up task.
  - `OnCompleteDressUpResponse(response)`: Processes server responses for dress-up tasks.

### 4. **Currency Management**

Tracks and modifies player currency, integrating with rewards and purchases.

#### Functions
- **Adding Currency**:
  - `AddCurrency(playerData, id, amount)`: Adds or updates currency amounts.
- **Spending Currency**:
  - `SpendCurrency(playerData, id, amount)`: Deducts a specified amount of currency.
  - `HasEnoughCurrency(playerData, id, amount)`: Verifies if the player has sufficient funds.
- **Retrieving Currency**:
  - `GetCurrencyAmount(playerData, id)`: Returns the amount of a specific currency.

### 5. **Quest Integration**

Manages quest progression, resets, and rewards.

#### Functions
- **Progression**:
  - `ProgressOnQuest(id, totalProgress)`: Updates progress for a specific quest.
  - `GetQuestData(id)`: Retrieves quest data by ID.
- **Resets**:
  - `RequestRestartQuests()`: Requests a reset of all player quests.
  - `OnRequestRestartData(player)`: Resets quests and reinitializes the player’s quest list.

### 6. **Event System**

The module utilizes a robust event-driven architecture to handle data flow.

#### Key Events
- **Data Events**:
  - `LoadDataRequestEvent`: Triggers data loading on the server.
  - `SaveDataRequestEvent`: Requests data saving from the client.
- **Dress-Up Events**:
  - `CompleteDressUpRequestEvent`: Sends a completion request for a dress-up task.
  - `CompleteDressUpResponseEvent`: Returns the results of a dress-up task.
- **Quest Events**:
  - `RestartQuestsRequestEvent`: Triggers a quest reset request.
  - `RestartQuestsResponseEvent`: Responds to quest reset requests.

## Workflow Examples

### Saving Player Data
1. Player modifies their data in-game.
2. `SavePlayerData` is called on the client.
3. `SaveDataRequestEvent` sends the data to the server.
4. `ServerSavePlayerData` validates and stores the data in persistent storage.

### Adding Rewards
1. A reward is earned through gameplay.
2. `ServerAddRewardsFromLootContainer` adds the reward to the player’s data.
3. The data is saved, and the updated state is sent to the client.

### Completing a Quest
1. Player progresses on a quest.
2. `ProgressOnQuest` updates the quest state.
3. The client requests a save via `SavePlayerData`.