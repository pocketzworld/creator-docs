# Lecture 12: NPCs

## Introduction

In this lecture, you'll learn how to add non-player characters (NPCs) to your game in Highrise Studio. NPCs make your game world more lively and interesting by letting players interact with various characters. This can deepen the gameplay and make the experience more engaging.

## What Are NPCs?

Non-player characters (NPCs) are characters in your game that players don't control. They can be friends or foes, offering quests, information, or challenges. NPCs are great for making your game world feel full and active.

## Creating NPCs

Here’s how you can set up NPCs in Highrise Studio:

1. **Right-click** in the **Hierarchy** panel and choose `Highrise > NPC`.
2. Click on the `NPC` prefab in the **Hierarchy** panel.
3. Press **(-)** to take out the default outfit "HumanoidDefault (Character Outfit)".
4. Follow these steps to customize how the NPC looks.

![NPC Outfit](/assets/learn/guides/studio/Lectures/npc-outfit.png)

### Customizing the NPC's Appearance

#### Step 1: Creating an NPC Outfit

1. **Right-click** in the Project View and make a new folder called `Characters`.
2. Inside the `Characters` folder, make another folder called `Outfits`.
3. Right-click in the `Outfits` folder and choose `Create > Highrise > Character > NPC Outfit`.
4. Name the outfit (e.g., `NPC_Outfit`) and select it in the Project View.
5. Click the "Open Outfit Editor" button in the Inspector while the outfit is selected.
6. Change the outfit by adding or removing clothes.
7. Save your changes with `CTRL + S` or `CMD + S`.

![Outfit Editor](/assets/learn/guides/studio/Lectures/outfit-editor.png)

#### Step 2: Assigning the Outfit to the NPC

1. Click on the NPC in the Hierarchy panel.
2. Drag the outfit from the Project View to the "Outfit" field in the Inspector.

You can design several outfits for one NPC, allowing you to change their look for different parts of your game.

![Assign Outfit](/assets/learn/guides/studio/Lectures/assign-outfit.png)

## Outfit Editor

The Outfit Editor in Highrise Studio lets you customize the appearance of your characters. You can add, remove, and adjust clothing items to create unique outfits for your NPCs. It offers the following categories for customization:

- Skin Tone
- Front & Back Hair
- Eyes
- Eye Brows & Facial Hair
- Nose
- Mouth
- Face Accessories
- Tops
- Bottoms
- Full Body
- Headwear & Accessories
- Shoes
- Auras & Customizations

![Outfit Editor Window](/assets/learn/guides/studio/Lectures/outfit-editor-window.png)

## YouTube Tutorial

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/MNc1Q4As5bA" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Conclusion

NPCs add a rich layer of interaction and detail to your game, enhancing the overall experience. By creating and customizing NPCs in Highrise Studio, you can shape a more immersive world for players to explore. After setting up your NPCs, continue to [Lecture 13: Emotes](https://create.highrise.game/learn/studio/create/beginner-guide/lecture-thirteen) to learn how to make your NPCs perform animation in game.