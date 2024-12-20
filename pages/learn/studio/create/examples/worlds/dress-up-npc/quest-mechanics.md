# Quest Mechanics

This document provides a comprehensive overview of the quest mechanics implemented in the game, explaining how players interact with quests, how they are structured, and how the system is designed in the codebase.

## Overview

Quests are a key gameplay feature, designed to guide players through objectives, provide engagement, and reward progress. The quest system supports features such as:

- Interaction with NPCs to receive quests.
- Progress tracking for individual quests.
- Completion rewards, including in-game items or currency.
- Sequential and non-linear quest lines.
- Integration with other gameplay systems like dress-up tasks and rewards.

## Core Concepts

### 1. **Quest Structure**

Quests are defined using the `QuestTemplate.lua` and grouped into quest lines through the `QuestLineTemplate.lua`. The `QuestManager.lua` handles the progression and management of quests.

#### Quest Attributes
Each quest includes:
- **ID** (`_id`): A unique identifier for the quest.
- **Text** (`_questText`): The main text describing the quest.
- **Goal Description** (`_goalDescription`): A detailed explanation of the objective.
- **Target Amount** (`_targetAmount`): The required progress to complete the quest.
- **Requirement** (`_requirement`): Conditions for completing the quest, such as a specific task.
- **Loot** (`_lootContainerTemplate`): Rewards provided upon completion.

#### Key Functions
- `GetId`: Retrieves the quest ID.
- `MeetsReqs`: Checks if the requirements for the quest are met and returns the progress.

### 2. **Quest Lines**

Quest lines group related quests together. The `QuestLineTemplate.lua` provides functionality to manage these groupings.

#### Quest Line Attributes
- **ID** (`_id`): Unique identifier for the quest line.
- **Quests** (`_quests`): List of quests included in the quest line.

#### Key Functions
- `GetQuestTemplateById`: Retrieves a quest template by ID.
- `GetNextQuestInQuestLine`: Identifies the next quest in the sequence based on progress.

### 3. **Quest Manager**

The `QuestManager.lua` serves as the central controller for quests, handling initialization, progression, and events.

#### Responsibilities
- Loading and initializing quests.
- Tracking active quests.
- Checking quest completion and granting rewards.
- Managing quest-related UI updates.

#### Key Functions
- `LoadQuestInstances`: Loads quest instances based on saved data.
- `IsQuestComplete`: Checks if a quest is completed based on progress.
- `GrantQuestRewards`: Distributes rewards for completing a quest.
- `NotifyEventForQuests`: Updates quest progress based on player actions and triggers necessary events.

## Workflow

1. **Receiving a Quest**
   - Quests are typically initiated through NPC interactions. Players can accept quests via dialogue prompts handled by `DialogManager.lua` and `UIDialog.lua`.

2. **Tracking Progress**
   - Progress is updated in real-time through events. For example, a player completing a dress-up task will trigger the `MeetsReqs` function to update the quest state.

3. **Completing a Quest**
   - Once the target progress is achieved, `GrantQuestRewards` is called to provide rewards. The completed quest is marked, and the next quest in the line is activated if available.

4. **UI Updates**
   - The UI reflects the current quest state using HUD elements managed by `UIManager.lua`. Notifications and reward popups are displayed dynamically.

## Integration with Other Systems

### Dress-Up Tasks
Quests often require players to complete dress-up tasks. The `NPCDressUpTaskController` manages these interactions and ensures proper tracking of task-related quests.

### Rewards
The reward system is tightly integrated, allowing quests to provide meaningful incentives. Rewards are defined in the quest templates and distributed through the `RewardLoot` function.

### Save System
Progress is saved and loaded using the `SaveManager` module, ensuring players retain their progress across sessions.

## Implementation Details

### Example Quest Definition
```lua
local questTemplate = {
  _id = "quest_001",
  _questText = "Dress up your avatar for the themed party!",
  _goalDescription = "Choose an outfit matching the theme.",
  _targetAmount = 1,
  _requirement = DressUpRequirement,
  _lootContainerTemplate = LootContainer,
}
```

### Example Quest Line Definition
```lua
local questLineTemplate = {
  _id = "line_001",
  _quests = {quest_001, quest_002, quest_003},
}
```

## Key Events

### `QuestsLoadedEvent`
Triggered when quests are loaded. Used to initialize UI updates.

### `QuestCompletedEvent`
Triggered when a quest is completed. Used to display rewards and activate the next quest.

### `QuestDisplayActionEvent`
Triggered for actions related to quest progress display.

## Best Practices

1. **Modularity**: Keep quests and quest lines modular for easier updates and management.
2. **Descriptive Texts**: Use clear and engaging language for quest descriptions to enhance player experience.
3. **Testing**: Test quests thoroughly to ensure objectives and rewards align with gameplay goals.