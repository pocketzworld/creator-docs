# Lecture Four (Part Four): Scripts

## Introduction

Scripts are the brains behind the game objects in your Unity projects. By using Lua and Highrise's API, you can add intelligent behaviors to your game elements, manage interactions, and much more.

## What are Scripts?

Scripts in Unity, especially in Highrise Studio, are bits of code that tell your game objects what to do and when to do it. We use Lua to write these scripts because it’s simpler and integrates perfectly with the Highrise API.

You might think scripting is difficult or too complex to grasp, but it's really about repeating the same steps and practicing regularly. With a bit of patience, you'll soon get the hang of it. We provide tools, examples, and support to help you get started. Don't worry we'll be with you every step of the way.

<Note type="warning">
In this lecture, we'll only cover the basics of scripting and what you can achieve with it. Scripting is a broad topic, and we'll explore it in more detail in future lectures.
</Note>

## Basics of Using Lua Scripts

Scripts can control almost everything in your game:

### Step 1: Adding a Script
- **Create a folder**: Right-click in the Project Window, choose `Create` > `Folder`, and name it `Scripts`.
- **Create a Lua Script**: Right-click in the Scripts folder, choose `Create` > `Lua` > `Client` Script and name it `MyFirstScript`.
- **Attach the Script**: Drag the script from the Project Window onto the GameObject in the Hierarchy that you want to control.

![Script](/assets/learn/guides/studio/Lectures/gameobject-scripts.png)

### Step 2: Editing a Script

<Note type="warning">
You must have a code editor installed on your machine to edit scripts. We recommend using Visual Studio Code.
</Note>

- **Open the Script**: Double-click the script in the Project Window to open it.
- **Write Simple Code**: Use Lua to define what the GameObject will do, like moving, playing sounds, or interacting with players.

Here are a few things Lua scripts can do in Highrise Studio:

- **Store Data**: Keep track of player scores, game states, or inventory items.
- **Make Purchases**: Use in-game currency (gold) to buy items or unlock new game levels.
- **Build User Interfaces**: Create menus, buttons, and other interactive elements that players can use.

## Example: Basic Script

Let's write a simple script that makes a GameObject move:

```lua
--!Type(Client)

-- This Lua script is called when the script is first loaded
function self:Awake()
    -- Print a message to the console
    print("Hello World!")
end

-- This Lua script moves a GameObject up every frame
function self:Update()
    self.gameObject.transform.position = self.gameObject.transform.position + Vector3.up * Time.deltaTime
end
```

## Testing Your Script

To see your script in action, click the Play button in Unity. Your GameObject should start moving up in the scene. If it does, congratulations! You've just written and tested your first Lua script in Highrise Studio.

See? That wasn't so hard, was it? With a bit of practice, you'll be writing more complex scripts in no time. I bet if felt good when you saw your GameObject move? That's the magic of scripting!

<Note type="warning">
Make sure to sign in to your Highrise account in Unity. This will allow you to enter Play Mode as your avatar.
</Note>

## Script Types

There are a few different types of scripts you can use when making games in Highrise Studio:

- **Client Scripts**: These are like the puppeteers that work only on your device. They make sure that everything you see and play with in the game behaves correctly.
- **Server Scripts**: Think of these as the bosses who work behind the scenes on the game's server. They make sure everyone playing the game follows the rules, like keeping score and managing what you buy in the game.
- **ClientAndServer Scripts**: These are super versatile, working both on your device and the server. They help manage scores and purchases, making sure everything matches up perfectly wherever you play.
- **Module Scripts**: These are like toolboxes. They hold useful code bits that you can use over and over in different parts of your game.
- **UI Scripts**: These scripts are all about making things you can touch and use in the game, like menus and buttons.

This is a quick look at the types of scripts. We'll learn more about them as we go. If you're curious and want to know more right now, you can read this article: [Learn about script types](https://create.highrise.game/learn/studio/create/scripting/script-types/overview)

## Why Scripts Matter

Scripts bring your game to life. Without them, your game objects would just sit there. With scripts, they can interact, react, and engage players in countless ways.

## Conclusion

Scripts are a powerful tool in your game development arsenal, especially when using Lua in Highrise Studio. They make your game interactive and fun, allowing you to implement complex game logic with ease.

## Next Steps

Experiment with different scripts to see how they affect your game. Try new things and see what you can create. Remember, every great game starts with a simple line of code.

- [Lecture Four (Part Five): Scenes](https://create.highrise.game/learn/studio/basics/beginner-guide/lecture-four/lecture-four-part-five)