# Loot Mechanics

This document provides an overview of the loot mechanics implemented in the game, detailing how loot is defined, managed, and distributed.

## Overview

The loot system governs the distribution of rewards in the game, such as currency, clothing items, and collections. It ensures a balance between guaranteed and randomized rewards, enhancing the player’s engagement and sense of accomplishment.

Key features include:
- Guaranteed loot rewards for specific actions or milestones.
- Randomized additional loot to introduce variety.
- Weighted probability for additional rewards.
- Integration with other gameplay systems, such as quests and events.

## Core Concepts

### 1. **Loot Containers**

Loot containers serve as the primary structure for defining and managing rewards. Each container specifies guaranteed rewards and additional items with probabilities.

#### Loot Container Attributes
- **Guaranteed Loot List** (`_guaranteedLootList`): Items guaranteed to be included in the reward.
- **Guaranteed Loot Ranges** (`_guaranteedLootRanges`): Quantity ranges for each guaranteed item.
- **Additional Loot Count Range** (`_additionalLootCountRange`): Number of additional items to include, selected randomly.
- **Additional Loot List** (`_additionalLootList`): Items eligible for random inclusion.
- **Additional Loot Ranges** (`_additionalLootRanges`): Quantity ranges for each additional item.
- **Additional Loot Weights** (`_additionalLootWeights`): Probabilities for selecting each additional item.

#### Key Functions
- `GetGuaranteedLootList`: Retrieves the guaranteed loot items.
- `GetGuaranteedLootRanges`: Retrieves the quantity ranges for guaranteed loot.
- `GetAdditionalLootCountRange`: Retrieves the range for the number of additional items.
- `GetAdditionalLootList`: Retrieves the additional loot items.
- `GetAdditionalLootWeights`: Retrieves the weights for additional items.

### 2. **Loot Items**

Loot items represent the individual rewards within the loot system. They can include:
- **Currency**: In-game currency rewards.
- **Clothing**: Individual clothing items.
- **Collections**: Bundles of themed clothing items.

#### Reward Template Logic
The reward template determines the type of item distributed. Key logic includes:
- Prioritizing specific reward templates (e.g., clothing over currency).
- Returning `nil` if no reward template is defined.

### 3. **Loot Manager**

The `LootManager.lua` handles the primary logic for distributing rewards, ensuring that all conditions and probabilities are adhered to.

#### Responsibilities
- Calculating guaranteed rewards.
- Determining additional rewards based on weights.
- Returning a finalized list of rewards.

#### Key Functions
- `GetRandomAmount`: Generates a random quantity within a specified range.
- `Roll`: The main function to generate a list of rewards from a loot container.
- `AddRewardToList`: Adds rewards to a list, merging stackable items if applicable.
- `GetRewardInList`: Finds and updates existing rewards in a list.

## Workflow

1. **Creating a Loot Container**
   - Define guaranteed items and their ranges.
   - Specify additional items, their ranges, and weights.

2. **Rolling for Rewards**
   - Call `Roll` with the appropriate loot container.
   - Guaranteed rewards are added first.
   - Additional rewards are determined based on weighted probabilities.

3. **Distributing Rewards**
   - The final reward list is passed to the relevant gameplay system (e.g., quest completion or event rewards).

## Example Implementation

### Example Loot Container
```lua
local lootContainer = {
  _guaranteedLootList = {currencyReward, clothingItem},
  _guaranteedLootRanges = {Vector3.new(10, 20), Vector3.new(1, 1)},
  _additionalLootCountRange = Vector3.new(1, 3),
  _additionalLootList = {extraClothing, rareItem},
  _additionalLootRanges = {Vector3.new(1, 2), Vector3.new(0, 1)},
  _additionalLootWeights = {75, 25},
}
```

### Rolling for Rewards
```lua
local rewards = LootManager.Roll(lootContainer)
for _, reward in ipairs(rewards) do
  print("Reward:", reward.Template.Id, "Amount:", reward.Amount)
end
```

## Key Events

### Guaranteed Loot
Ensures players always receive core rewards, maintaining predictability for critical gameplay moments.

### Additional Loot
Adds excitement and variability, using weights and ranges to balance rarity and accessibility.