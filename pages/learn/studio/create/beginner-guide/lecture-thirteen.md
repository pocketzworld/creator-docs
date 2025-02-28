# Lecture 13: Emotes

## Introduction

In this lecture, you'll discover how to get your NPCs to perform emotes in Highrise Studio. Emotes are animations that show emotions or actions, making your characters more lively and interesting. This can make your NPCs more fun and engaging for players.

## What Are Emotes?

Emotes are animations that characters use to express feelings, actions, or reactions. They are often used in games to help characters show how they feel, interact with players, or react to things happening around them. Emotes can be simple like a wave or a nod, or more complex like dancing or doing tricks.

## Adding Emotes to NPCs

Here's a simple way to give emotes to your NPCs in Highrise Studio:

1. Make a new folder named `Scripts` in the Project View.
2. Right-click in the `Scripts` folder and go to `Create` > `Lua` > `Client`.
3. Name the script (e.g., `EmoteScript`) and open it in the Code Editor.
4. Write a Lua script that will start the emote animation you want for your NPC.

```lua
--!Type(Client)

--!SerializeField
local emote_ids : { string } = {} -- List of emote IDs.
--!SerializeField
local is_loop : boolean = false -- Should the emotes loop?

function self:Awake()
    local character = self.gameObject:GetComponent(Character)
    if not character then
        print("No Character component found on " .. self.gameObject.name)
        return
    end

    local function playEmote()
        if #emote_ids == 0 then
            print("No emotes to play on " .. self.gameObject.name)
            return
        end

        -- Pick a random emote and play it.
        local emoteIndex = math.random(1, #emote_ids)
        character:PlayEmote(emote_ids[emoteIndex], false, function()
            -- If it should loop, play another emote after this one.
            if is_loop then
                playEmote() -- Calls itself to start another emote.
            end
        end)
    end

    playEmote()
end
```

### Attaching the Emote Script to an NPC

1. Click on the NPC in the Hierarchy panel.
2. Drag the `EmoteScript` from the Scripts folder and drop it onto the NPC in the Inspector.
3. Set up the script's settings like which emotes to use and whether they should loop.

![Emote Script](/assets/learn/guides/studio/Lectures/emote-script-component.png)

### Finding Emote IDs

To get the emote IDs you need:

1. Open the outfit you made before by double-clicking it.
2. Click the Outfit Editor in the Inspector.
3. Click the `Emotes` icon to open the Emote Editor.
4. Note down the emote IDs from the Emote Editor to use in your script.

![Emotes Editor](/assets/learn/guides/studio/Lectures/emotes-editor.png)

### Setting Up the Emote Script

To set which emotes your NPC will use and if they should keep repeating:

1. Click on the NPC that has the `EmoteScript`.
2. Turn on `is_loop` if you want the emote to keep going.
3. Put the emote IDs you want into the `emote_ids` array.

![Emote List](/assets/learn/guides/studio/Lectures/emote-list.png)

<Note type="info">
If you want the NPC to keep doing the same emote over and over, just put one emote ID in the `emote_ids` array.
</Note>

## YouTube Tutorial

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/2tKOxUUQLv4" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Conclusion

Emotes are a great way to give your NPCs personality and make them interactive. By using the steps in this guide, you can create characters that are not just fun to watch but also add to the storytelling in your game. Try different emotes and settings to see how they can make your game world more lively and memorable for players.

## Next Steps

- [Lecture 14: Publishing Your Game](https://create.highrise.game/learn/studio/create/beginner-guide/lecture-fourteen)