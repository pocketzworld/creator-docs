# Folder Structure

## Overivew

This document explains the structure of the project and the purpose of each folder.


## Core Project Folders

- **Art**
Home to all visual assets like character designs, backgrounds, and icons.
*Example*: Player and NPC sprites, decorative assets for environments.

- **Audio**
Everything your ears need! Includes sound effects and background music.
*Example*: Button click sounds, ambient town noises.

- **Fonts**
Fonts used throughout the game, ensuring every text element looks just right.
*Example*: Stylish fonts for NPC dialogues or UI labels.

- **Materials & Mesh**
  - Materials: Textures and shaders to give life to 3D models.
  - Mesh: The 3D structures for characters and objects.

- **Music**
All the soundtracks that set the mood of the game.
*Example*: Upbeat music for the dress-up area or soft tones in the background.

- **NPCs**
This folder houses all the lovable (or not-so-lovable!) characters that populate your game world.

- **Prefabs**
Ready-to-use templates for objects like interactable items, NPCs, and environmental props.

- **Scenes**
The heart of the game. Contains the layouts and the scenes where the game unfolds.

- **ScriptableObjects**
Scriptable data assets to store configurations or game data.
*Example*: Settings for dress-up tasks or NPC dialogue options.

- **Scripts**
The brain behind the project! Contains the code that powers gameplay, UI, and interactions.
*Key scripts include*:
  - `GameManager.lua`: Orchestrates game logic.
  - `UIDressUp.lua`: Powers the dress-up menu UI.

## External Asset Folders

- **Downloads**
A collection of resources sourced from the Highrise Assets Catalog for use in the project.

- **JMO Assets, PolyPerfect, StylizedFountains, KawaiiCity**
External assets added to enhance the world. Think of these as the guest stars in your project, bringing unique touches to the game design.

## Utility Folders (Studio Specific)

- **Resources**
Unity's go-to folder for dynamically loaded assets. Think of it as a hidden stash for runtime goodies.

## Visualizing the Structure

├── Art/
├── Audio/
├── Downloads/
├── Fonts/
├── JMO Assets/
├── KawaiiCity/
├── Materials/
├── Mesh/
├── Music/
├── NPCs/
├── PolyPerfect/
├── Prefabs/
├── Resources/
├── Scenes/
├── ScriptableObjects/
├── Scripts/
│   ├── Core/
│   │   ├── GameManager.lua - Orchestrates game logic.
│   │   ├── SaveManager.lua - Manages saving and loading.
│   ├── UI/
│   │   ├── UIDressUp.lua - Handles the main dress-up interface.
└── StylizedFountains/

## Next Steps

Now that you understand the project structure, let's dive into the core gameplay mechanics and how to interact with the game world. Continue to the [Gameplay Mechanics](https://create.highrise.game/learn/studio/create/examples/worlds/dress-up-npc/gameplay-mechanics) guide to learn more.