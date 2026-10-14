# Build a World with an AI Agent

AI coding agents such as [Claude Code](https://www.claude.com/product/claude-code) and [Codex](https://openai.com/codex/) can build your world from a description, working in a Highrise Studio project you have open in Unity. This guide shows how to get started.

## Step 1: Create and Open a Project

Create a project in Studio Hub and open it in Unity, as described in [Getting Started](/learn/studio/basics/getting-started).

When the project opens, Highrise Studio adds a `CLAUDE.md` and an `AGENTS.md` file to the project's folder. These files tell an agent how to work in the project.

## Step 2: Start Your Agent

1. Open a terminal in the project's folder, for example `Documents/Highrise Studio/Projects/My World`.
2. Start Claude Code or Codex.
3. Describe the world you want, for example: "Build me a Highrise world where players race to collect coins."

## What the Agent Does

The agent uses the project's launcher, `Library/Highrise/hr`. It runs `Library/Highrise/hr hr_guide` first, which teaches it how to build Highrise worlds, and then uses Highrise Studio's commands to edit scenes, write Lua scripts, and play-test the world in Unity.

## Good to Know

- The commands need the Unity command line tools. If they are missing, the agent asks before installing them.
- Highrise Studio's commands only work while the project is open in Unity. If Unity is closed, the agent runs `Library/Highrise/hr open` to open it.
- If Unity asks for permission or shows a dialog, answer it: the agent can't.

When your world is ready, test it with the **Play** button in Unity and publish it as described in [Getting Started](/learn/studio/basics/getting-started).
