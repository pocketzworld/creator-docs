# Build a World with an AI Agent

AI coding agents such as [Claude Code](https://www.claude.com/product/claude-code) and [Codex](https://openai.com/codex/) can create a Highrise Studio project, open it in Unity, and build your world from a description. This guide shows how to get started.

## Step 1: Install Studio Hub

Download and install [Studio Hub](https://create.highrise.game/highrise-studio), then open it once. For details, see [Getting Started](/learn/studio/basics/getting-started).

Studio Hub creates the **Highrise Studio** folder in your Documents folder and keeps a `CLAUDE.md` and an `AGENTS.md` file there. These files tell an agent how to create a project and how to work in one.

## Step 2: Start Your Agent

1. Open a terminal in your **Highrise Studio** folder (`Documents/Highrise Studio`). Any other folder also works.
2. Start Claude Code or Codex.
3. Describe the world you want, for example: "Build me a Highrise world where players race to collect coins."

## What the Agent Does

To create a project, the agent runs Highrise's bootstrap script. On macOS:

```sh
curl -fsSL https://raw.githubusercontent.com/pocketzworld/studio-ai/main/start/hr | sh -s -- new "Projects/My World"
```

On Windows, in PowerShell:

```powershell
& ([scriptblock]::Create((irm https://raw.githubusercontent.com/pocketzworld/studio-ai/main/start/hr.ps1))) new "Projects\My World"
```

The script creates the project from a Highrise template, sets it to the latest Highrise Studio package, opens it in Unity, and waits until Highrise Studio is ready. To list the templates, the agent runs the script with `templates` in place of `new`. To bring an existing project up to date, it runs the script with `upgrade "<project folder>"`.

Inside a project, the agent uses the project's own launcher, `Library/Highrise/hr`. It runs `Library/Highrise/hr hr_guide` first, which teaches it how to build Highrise worlds, and then uses Highrise Studio's commands to edit scenes and write Lua scripts.

## Good to Know

- The agent installs the Unity command line tools itself if they are missing. It asks before installing a Unity editor, which is a large download.
- Unity must be allowed to open. If your computer asks for permission, allow it.
- Highrise Studio's commands only work while the project is open in Unity. If Unity is closed, the agent runs `Library/Highrise/hr open` to open it.

When your world is ready, test it with the **Play** button in Unity and publish it as described in [Getting Started](/learn/studio/basics/getting-started).
