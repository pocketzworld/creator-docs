# Mac Python SDK Setup

This tutorial will guide you step-by-step, from installing the Python development environment, the SDK and its dependencies, to launching your first Highrise bot on a Mac.

We encourage you to follow along with the video tutorial to ensure a successful setup. Your journey into Highrise bot development starts here.

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/q8NYI8NYfgA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## **Step 1: Installing Homebrew**

Homebrew is a package manager for MacOS that we use to install Python and other tools.

1. Go to the Homebrew website at **[brew.sh](https://brew.sh/)** in a web browser.
2. On the Homebrew homepage, you'll see an install command. Copy this command.
3. Open your Mac terminal and paste the install command there.
4. Press Enter to start the installation. The process may take about 5 to 10 minutes.

## **Step 2: Installing Python 3.11**

With Homebrew installed, we can now install Python.

1. In the terminal, enter the command **`brew install python@3.11`**.
2. Press Enter to start the Python installation.

## **Step 3: Installing the Highrise Python SDK**

Before installing the SDK, navigate to the directory where you plan to build your bot.

1. In your chosen directory, we need to set up a Python virtual environment. This helps manage Python dependencies for your project. Enter the command **`python3.11 -m venv .venv`** in the terminal.
2. Now, we activate the virtual environment with the command **`source .venv/bin/activate`**.
3. We're ready to install the Highrise Python SDK. Enter the command **`pip install highrise-bot-sdk==24.1.0`**. Replace **`24.1.0`** with the latest version number of the SDK. The latest version can be found on the Highrise Create Portal.

## **Step 4: Writing Your Bot Code**

Now we can start writing our bot's code.

1. In your chosen directory, created a python file called **`echo.py`**.
2. Open this file and write your bot code in it. An example bot called **[Echo](https://create.highrise.game/learn/guides/bots/examples/basics)** is available on the Highrise documentation, which simply prints activities happening in a Highrise room into the terminal.
3. Save your code in the Python file.

## **Step 5: Running Your Bot**

Finally, we are ready to run our bot.

1. You'll need your Highrise API token and the Room ID where you want to deploy your bot. You can obtain the API token from the Highrise Create Portal, under _Dashboard_ and _Credentials_, and the Room ID from the Highrise app. In the app, navigate to the room you're interested in and click on "Share this room". A url will be generated that includes your Room ID.
2. In the terminal, make sure you're in the directory where your bot's Python file is. Enter the command **`highrise <filename>:<class_name> <room_id> <api_token>`**. Replace `<filename>`, `<class_name>` with the bot’s file name and the name of the class that implements the Highrise Basebot (most likely `Bot`), along as **`<room_id>`** and **`<api_token>`** with your actual Room ID and API token respectively.
3. Press Enter to run the bot.

With this setup, your bot should now be up and running, echoing what it sees happening in the Highrise room in the terminal.
