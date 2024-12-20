# GameSettings Module Documentation

The `GameSettings.lua` module provides centralized management of templates and configurations that define various game elements. It ensures consistency, validation, and easy access to critical data structures.

## Overview

The `GameSettings` module manages:

- Templates for currencies, clothing, quests, and store items.
- Dialog configurations for events such as quest completions and resets.
- Validation of unique and valid IDs for all templates.
- Configuration of gameplay parameters such as success thresholds and audio effects.

## Key Components

### 1. **Templates Management**

#### Currency Templates
- Stores details about in-game currencies.
- **Access Function**: `GetCurrencyTemplate(id)` retrieves a specific currency by its ID.

#### Clothing Templates
- Defines individual clothing items and their properties.
- **Access Function**: `GetClothingTemplate(id)` retrieves a clothing template by ID.

#### Clothing Collection Reward Templates
- Manages collections of clothing items as rewards.
- **Access Function**: `GetClothingCollectionRewardTemplate(id)` retrieves a collection reward template by ID.

#### Store Item Templates
- Defines items available in the in-game store.
- **Access Functions**:
  - `GetItemStoreTemplate(id)`: Retrieves a store item template by ID.
  - `GetStoreItems()`: Retrieves all store items.

#### Quest Templates
- Defines quests within quest lines.
- **Access Functions**:
  - `GetQuestTemplate(id)`: Retrieves a quest by ID.
  - `GetQuestTemplateByIndex(mainQuestLineIndex, index)`: Retrieves a quest by its position in a quest line.
  - `GetAllQuestLines()`: Retrieves all quest lines.

#### Dress-Up Tasks
- Represents tasks for players to complete using the dress-up system.
- **Access Functions**:
  - `GetDressUpTask(id)`: Retrieves a dress-up task by ID.
  - `GetDressUpTaskByIndex(index)`: Retrieves a dress-up task by its position in the list.

### 2. **Validation System**

#### Template Validation
Ensures all templates have unique and valid IDs to avoid conflicts and errors.

**Function**: `Validate()`
- Validates:
  - Currencies
  - Clothing
  - Clothing collections
  - Store items
  - Quest lines
  - Dress-up tasks.

**Key Logic**:
- IDs must not be nil or empty.
- No two templates within the same list can share the same ID.
- Errors are logged with detailed information for debugging.

### 3. **Dialog Configurations**

Defines dialog templates for various game scenarios:
- **Reset Quests**: `GetResetDialog()` retrieves the dialog for resetting quests.
- **Quest Completion**: `GetQuestCompleteDialog()` retrieves the dialog for completed quests.
- **Quest Not Unlocked**: `GetQuestNotUnlockedDialog()` retrieves the dialog for locked quests.

### 4. **Gameplay Configuration**

#### Success Thresholds
- **Function**: `GetPercentChoicesCorrectToSucceed()`
- Returns the percentage of correct choices required to succeed in tasks (default: `0.9`).

#### Audio Effects
- **Function**: `GetDressUpSuccessSound()`
- Returns the audio shader played upon successful completion of a dress-up task.

## Workflow Examples

### Adding a New Template
1. Define the new template and ensure it has a unique ID.
2. Add the template to the appropriate list (e.g., `_currencyList`, `_clothingList`).
3. Use `Validate()` to check for ID conflicts.

### Accessing Templates
1. To retrieve a currency template by ID:
   ```lua
   local currency = GetCurrencyTemplate("gold")
   if currency then
       print("Currency Name: ", currency.Name)
   end
   ```

2. To retrieve all store items:
   ```lua
   local items = GetStoreItems()
   for _, item in ipairs(items) do
       print("Item Name: ", item.Name)
   end
   ```

### Validating Templates
1. Call `Validate()` during game initialization.
   ```lua
   GameSettings.Validate()
   ```
2. Check logs for validation errors and resolve them before proceeding.