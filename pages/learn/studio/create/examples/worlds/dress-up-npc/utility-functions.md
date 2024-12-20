# Utility Functions

This document serves as an overview and reference guide for various utility functions and modules implemented across the game. These utilities provide foundational support for core gameplay and system functionalities.

## Overview

Utility modules encapsulate common functions, tools, and helper methods that streamline game development. They include operations for:

- Mathematical calculations.
- Animation and tweening.
- Data manipulation.
- Character fading and object handling.
- UI adjustments and visual enhancements.

## Core Utilities

### 1. **General Utility Functions**

#### Common Table Operations
- `IsInTable(t, value)`: Checks if a value exists in a table.
- `GetIndexInTable(t, value)`: Finds the index of a value in a table.
- `RemoveInTable(t, value)`: Removes a specific value from a table.
- `FindInTable(t, predicate)`: Finds the first element in a table matching a condition.

#### String Utilities
- `IsStringNullOrEmpty(s)`: Determines if a string is empty or nil.

#### Table Utilities
- `DeepCopy(original)`: Creates a deep copy of a table.
- `IsTableEqual(t1, t2, ignore_mt)`: Compares two tables for equality.

#### Randomization
- `GetRandomValueFromVector2(vector)`: Generates a random number within a `Vector2` range.

#### Time Utilities
- `GetDateString(seconds)`: Converts seconds to a formatted date string.
- `GetTimerText(seconds)`: Converts seconds to a formatted timer string.
- `GetTimeEndedAgo(endedSeconds)`: Returns a human-readable time elapsed string.

### 2. **Character Utilities**

#### Character Fade Helper
Provides smooth fade-in and fade-out effects for characters.

##### Key Functions
- `StartFade(character, fade, duration)`: Starts a fade effect on a character.
- `ShowShadow(character, show)`: Toggles the visibility of a character's shadow.

### 3. **Tweening and Animation**

#### Tween Module
Facilitates smooth animations and transitions for UI and objects.

##### Key Features
- Easing Functions:
  - `easeInQuad`, `easeOutQuad`, `easeInOutSin`, `easeInBack`, `easeOutBack`.
- Tween Configuration:
  - `FromTo(from, to)`: Sets start and end values.
  - `Duration(duration)`: Specifies the duration.
  - `Easing(easing)`: Applies an easing function.
  - `Loop()`: Enables looping for the tween.

#### Float Tween
Handles single-value tweening for numerical properties like transparency or movement.

### 4. **Outfit Utilities**

#### Outfit Serialization
Handles the conversion of clothing data between formats.

##### Key Functions
- `SerializeOutfitToData(outfit)`: Converts an outfit to a serializable data format.
- `DeserializeClothingDataToOutfit(clothingDataList)`: Converts clothing data to an outfit.
- `DeserializeOutfitSaveDataToOutfit(saveData)`: Converts save data into an outfit.

### 5. **Camera and UI Utilities**

#### Camera Cutscene Settings
Manages camera transitions and positioning during cutscenes.

##### Key Attributes
- `GetPitch()`, `GetZoom()`, `GetDuration()`, `GetTargetOffset()`: Retrieve respective camera settings.

#### Billboard Utility
Ensures game objects face the camera, commonly used for UI or indicators.

##### Key Functions
- `LateUpdate()`: Adjusts an object’s rotation to face the camera.

### 6. **Chat Dispatcher**

Handles chat events and visibility for text-based communication in the game.

##### Key Functions
- `EnableShowingMessages(show)`: Toggles the display of chat messages.
- `FindAndHideUIWorld(element, searchChildren, show)`: Hides or shows the `UIWorld` element.