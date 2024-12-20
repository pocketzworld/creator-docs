# Dialog Mechanics

This document provides a detailed overview of the dialog mechanics implemented in the game, explaining how dialogs are structured, managed, and presented to players.

## Overview

The dialog system enables interactive storytelling through NPC interactions, providing players with meaningful engagement and narrative progression. It supports:
- Multiple dialog steps with optional player responses.
- Dynamic nameplate and audio integration.
- Animation and emote support.
- Flexible customization for dialogs and character interactions.

## Core Concepts

### 1. **Dialog Templates**

Dialog templates define the structure and content of dialogs. Each template consists of multiple steps, which guide the flow of conversations.

#### Attributes
- **Dialog Strings** (`_dialogStrings`): The lines of dialog for each step.
- **Emotes** (`_emotes`): Character emotes displayed during each step.
- **Player Speaking List** (`_playerSpeakingList`): Indicates whether the player is speaking in each step.
- **Speech Audio** (`_speechAudio`): Audio associated with the dialog.
- **Display Data** (`_displayData`): Information for UI display, such as the speaker’s name.
- **Randomized Strings** (`_randomizeStrings`): If enabled, selects a random dialog string from the list.

#### Key Functions
- `GetDialogStep`: Retrieves a specific dialog step with all its attributes.
- `GetStepCount`: Returns the total number of steps in the dialog.
- `GetSpeechAudio`: Provides the audio associated with the dialog.
- `GetDisplayData`: Returns the display information for UI rendering.

### 2. **Dialog Manager**

The `DialogManager.lua` handles dialog initiation, progression, and completion.

#### Responsibilities
- Initializing and displaying dialogs.
- Managing the transition between dialog steps.
- Handling callbacks for dialog completion.
- Supporting dialog overrides for specific scenarios.

#### Key Functions
- `CreateDialogUI`: Initializes the dialog UI.
- `StartDialog`: Starts a dialog with a specified template and NPC.
- `EndDialog`: Ends the current dialog and cleans up resources.
- `ShowDialogStep`: Displays the current step of the dialog.
- `OnDialogStepComplete`: Progresses to the next dialog step or ends the dialog if completed.

### 3. **UI Dialog**

The `UIDialog.lua` script manages the visual presentation of dialogs, ensuring a seamless and engaging player experience.

#### Attributes
- **Dialog Text** (`_dialogText`): The main dialog content displayed to the player.
- **Nameplate** (`_nameText`): Displays the name of the speaker.
- **Animations**: Includes animations for text, nameplates, and arrows.
- **Audio Integration**: Synchronizes speech audio with dialog text.

#### Key Functions
- `Init`: Initializes the dialog system and registers callbacks.
- `NextDialogStep`: Updates the UI for the current dialog step.
- `AnimateNextCharacter`: Animates text character by character for a typewriter effect.
- `PlayEmote`: Plays emotes associated with the dialog step.
- `SetOverrideSpeech`: Allows for custom audio and display data overrides.

## Workflow

1. **Dialog Initialization**
   - Use `StartDialog` to initiate a dialog with an NPC, passing the template and callback.
   - `CreateDialogUI` ensures the dialog UI is ready.

2. **Step Progression**
   - Each step is displayed using `ShowDialogStep`.
   - `OnDialogStepComplete` handles transitions to the next step or ends the dialog.

3. **UI and Audio Integration**
   - The UI updates dynamically with speaker names, dialog text, and animations.
   - Speech audio synchronizes with dialog progression.

4. **Dialog Completion**
   - Once all steps are completed, `EndDialog` cleans up resources and triggers the completion callback.

## Example Implementation

### Example Dialog Template
```lua
local dialogTemplate = {
  _dialogStrings = {"Hello, adventurer!", "Are you ready for your quest?"},
  _emotes = {"wave", "nod"},
  _playerSpeakingList = {false, true},
  _speechAudio = adventureSpeech,
  _displayData = npcDisplayData,
}
```

### Starting a Dialog
```lua
DialogManager.StartDialog(dialogTemplate, npcCharacter, function()
  print("Dialog complete!")
end)
```

## Key Features

### Dynamic Animations
- **Typewriter Effect**: Dialog text appears character by character for immersion.
- **Nameplate Rotation**: Nameplates animate to indicate the active speaker.
- **Arrow Movement**: Indicates progression to the next step.

### Emote Integration
Characters can play emotes synchronized with dialog steps, enhancing engagement.

### Override Support
Dialog content and audio can be overridden dynamically for specific scenarios, such as quest-specific interactions.