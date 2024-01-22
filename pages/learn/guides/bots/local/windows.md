# Windows Python SDK Setup

This tutorial will guide you step-by-step, from installing the Python development environment, the SDK and its dependencies, to launching your first Highrise bot on a Windows machine.

We encourage you to follow along with the video tutorial to ensure a successful setup; the written instructions are also below. Your journey into Highrise bot development starts here.

<iframe width="560" height="315" src="https://www.youtube.com/embed/q8NYI8NYfgA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## **Step 1: Installing Python**

1. Go to the official Python website: **[Python.org](https://www.python.org/)**.
2. Navigate to the **`Downloads`** menu and select **`Windows`**.
3. Download Python version 3.11, which is currently recommended for the Highrise Python SDK. (as of May 2023)
4. Once downloaded, execute the installer.
5. During installation, ensure to tick the box that adds Python to your system PATH. This makes Python accessible from any location in the command prompt.
6. Choose **`Install Now`** and wait until the installation process completes.

## **Step 2: Setting Up the Highrise Python SDK**

1. Open the command prompt and navigate to the directory where you plan to develop your Highrise bot. It's recommended to create a dedicated folder for this project.
2. Open the directory with your preferred code editor (e.g., Visual Studio Code).
3. Create a virtual environment in your project directory. Virtual environments allow you to isolate your Python setup on a per-project basis. To create a virtual environment, type the following command in your command prompt:
    
    ```powershell
    python -m venv .venv
    ```
    
4. To activate the virtual environment, enter:
    
    ```powershell
    .venv\Scripts\activate
    ```
    
    The command prompt should now show the name of the virtual environment, indicating that it's active.
    
5. Install the Highrise Python SDK. Replace **`23.1.0.b10`** with the latest version, which can be found on the Highrise Create Portal:
    
    ```
    pip install highrise-bot-sdk==23.1.0.b10
    ```
    

## **Step 3: Creating Your Bot**

1. For this tutorial, we will use the **[Echo](https://create.highrise.game/learn/guides/bots/examples/basics)** bot example provided in the Highrise documentation. The Echo bot echoes events occurring in a Highrise room to the command line.
2. Create a new file in your project directory, named **`echo.py`**.
3. Copy the Echo bot code from the Highrise documentation into your **`echo.py`** file.

## **Step 4: Retrieving Your API Token and Room ID**

1. To run the bot, you'll need your Highrise API token and the Room ID.
2. You can obtain the API token from your account on the Highrise Create Portal, under *Dashboard*, and *Credentials*.
3. The Room ID is accessible within the Highrise app. Navigate to the room and click on the **`Share this room`** button in the info panel

<img src="https://cdn-production.joinhighrise.com/create-portal/room_ID_a5a157d527.jpg" alt="room ID" width="300" />

## **Step 5: Running Your Bot**

1. With the API token and Room ID in hand, you're ready to run your Echo bot. Use the following command, replacing **`<filename>`**, **`<class_name>`**, **`<room_id>`** and **`<api_token>`** with your file name, the class that implements the Highrise Basebot, and your actual Room ID and API token:
    
    ```powershell
    highrise <filename>:<class_name> <room_id> <api_token>
    ```
    

That's it! Your Echo bot is now active in your chosen Highrise room, and will echo events it perceives to your command line.