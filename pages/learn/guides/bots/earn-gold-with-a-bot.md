# Earn Gold with a Bot
Creating a Tipping Bot

This is a total beginner guide to hosting a simple bot to accept tips in your room. Tips sent to bots are automatically converted to Earned Gold, allowing you to exchange the gold for real money! For more info: [https://create.highrise.game/dashboard/creator-exchange](https://create.highrise.game/dashboard/creator-exchange)

This guide assumes you’re on an up to date Windows PC. You shouldn’t need any coding knowledge or tech understanding, just follow the steps closely to the end.

## Step 1: Install Python
Simply follow this link and download the latest Python version: [https://www.python.org/downloads/](https://www.python.org/downloads/)

You will get a .exe install file, locate it in your downloads and click the file. The following popup will show:

![python installation](https://cdn-production.joinhighrise.com/create-portal/install_python_d94b494f22.png)

**IMPORTANT**: Check the **‘Add python.exe to PATH’** tick box, then you can click **‘Install Now’** and follow the steps to install.

## Step 2: Installing your bot

First, create a folder where you want your bot files to be such as on your Desktop. Then create 2 files:

1. main.py - This is our Python code file which interacts with the Highrise SDK, making our bot perform its functionality.
2. startbot.bat - This file executes the code and runs your bot in one simple click.

and paste code below to the corresponding file.

`main.py`
```python
### FILL IN YOUR ROOM ID & API KEY HERE
room_id = "YOUR_ROOM_ID_HERE"
api_key  = "YOUR_API_TOKEN_HERE"

from highrise import BaseBot, __main__, CurrencyItem, Item, Position, AnchorPosition, SessionMetadata, User
from highrise.__main__ import BotDefinition
from asyncio import run as arun
from json import load, dump
import asyncio
import os

class Bot(BaseBot):
    def __init__(self):
        super().__init__()
        self.bot_id = None
        self.owner_id = None
        self.bot_status = False
        self.tip_data = None
        self.load_tip_data()
        self.bot_position = None

    async def on_chat(self, user: User, message: str) -> None:
        print(f"{user.username} said: {message}")
        response = await self.command_handler(user.id, message)
        if response:
            try:
                await self.highrise.chat(response)
            except Exception as e:
                print(f"Chat Error: {e}")

    async def on_whisper(self, user: User, message: str) -> None:
        print(f"{user.username} whispered: {message}")
        response = await self.command_handler(user.id, message)
        if response:
            try:
                await self.highrise.send_whisper(user.id, response)
            except Exception as e:
                print(f"Whisper Error: {e}")

    async def on_message(self, user_id: str, conversation_id: str, is_new_conversation: bool) -> None:
        conversation = await self.highrise.get_messages(conversation_id)
        message = conversation.messages[0].content
        response = await self.command_handler(user_id, message)
        if response:
            try:
                await self.highrise.send_message(conversation_id, response)
            except Exception as e:
                print(f"Messaging Error: {e}")

    # Handle commands from any source (chat/whisper/message)
    async def command_handler(self, user_id, message: str):
        if user_id != self.owner_id:  # Only listen to host's commands
            return
        command = message.lower().strip()

        if command.startswith("!set"): # Set the bot at your location
            set_position = await self.set_bot_position(user_id)
            return set_position
        elif command.startswith("!top"): # Build a 10 top tippers leaderboard
            top_tippers = self.get_top_tippers()
            formatted_tippers = []
            for i, (user_id, user_data) in enumerate(top_tippers):
                username = user_data['username']
                total_tips = user_data['total_tips']
                formatted_tippers.append(f"{i + 1}. {username} ({total_tips}g)")

            tipper_message = '\n'.join(formatted_tippers)
            return f"Top Tippers:\n{tipper_message}"
        elif command.startswith("!get "): # Query a specific user's tips
            username = command.split(" ", 1)[1].replace("@", "")
            tip_amount = self.get_user_tip_amount(username)
            if tip_amount is not None:
                return f"{username} has tipped {tip_amount}g"
            else:
                return f"{username} hasn't tipped."
        elif command.startswith("!wallet"): # Get Bot wallet gold
            wallet = await self.highrise.get_wallet()
            for currency in wallet.content:
                if currency.type == 'gold':
                    gold = currency.amount
                    return f"I have {gold}g in my wallet."
            return "No gold in wallet."

    async def on_tip(
        self, sender: User, receiver: User, tip: CurrencyItem | Item
    ) -> None:
        if isinstance(tip, CurrencyItem):
            print(f"{sender.username} tipped {tip.amount}g -> {receiver.username}")
            if receiver.id == self.bot_id:
                if sender.id not in self.tip_data:
                    self.tip_data[sender.id] = {"username": sender.username, "total_tips": 0}

                self.tip_data[sender.id]['total_tips'] += tip.amount
                self.write_tip_data(sender, tip.amount)

                if tip.amount >= 500:
                    await self.highrise.chat(f"Thank you {sender.username} for the generous {tip.amount}g tip!")

    async def on_user_join(self, user: User, position: Position | AnchorPosition) -> None:
        print(f"{user.username} joined the room")

    async def on_user_leave(self, user: User) -> None:
        print(f"{user.username} left the room")

    async def on_start(self, session_metadata: SessionMetadata) -> None:
        print("Bot Connected")
        self.bot_id = session_metadata.user_id
        self.owner_id = session_metadata.room_info.owner_id
        if self.bot_status:
            await self.place_bot()
        self.bot_status = True

    # Return the top 10 tippers
    def get_top_tippers(self):
        sorted_tippers = sorted(self.tip_data.items(), key=lambda x: x[1]['total_tips'], reverse=True)
        return sorted_tippers[:10]

    # Return the amount a particular username has tipped
    def get_user_tip_amount(self, username):
        for _, user_data in self.tip_data.items():
            if user_data['username'].lower() == username.lower():
                return user_data['total_tips']
        return None

    # Place bot on start
    async def place_bot(self):
        while self.bot_status is False:
            await asyncio.sleep(0.5)
        try:
            self.bot_position = self.get_bot_position()
            if self.bot_position != Position(0, 0, 0, 'FrontRight'):
                await self.highrise.teleport(self.bot_id, self.bot_position)
                return
        except Exception as e:
            print(f"Error with starting position {e}")

    # Write tip event to file
    def write_tip_data(self, user: User, tip: int) -> None:
        with open("./data.json", "r+") as file:
            data = load(file)
            file.seek(0)
            user_data = data["users"].get(user.id, {"total_tips": 0, "username": user.username})
            user_data["total_tips"] += tip
            user_data["username"] = user.username
            data["users"][user.id] = user_data
            dump(data, file)
            file.truncate()

    # Set the bot position at player's location permanently
    async def set_bot_position(self, user_id) -> None:
        position = None
        try:
            room_users = await self.highrise.get_room_users()
            for room_user, pos in room_users.content:
                if user_id == room_user.id:
                    if isinstance(pos, Position):
                        position = pos

            if position is not None:
                with open("./data.json", "r+") as file:
                    data = load(file)
                    file.seek(0)
                    data["bot_position"] = {
                        "x": position.x,
                        "y": position.y,
                        "z": position.z,
                        "facing": position.facing
                    }
                    dump(data, file)
                    file.truncate()
                set_position = Position(position.x, (position.y + 0.0000001), position.z, facing=position.facing)
                await self.highrise.teleport(self.bot_id, set_position)
                await self.highrise.teleport(self.bot_id, position)
                await self.highrise.walk_to(position)
                return "Updated bot position."
            else:
                return "Failed to update bot position."
        except Exception as e:
            print(f"Error setting bot position: {e}")

    # Load tip data on start
    def load_tip_data(self) -> None:
        with open("./data.json", "r") as file:
            data = load(file)
            self.tip_data = data["users"]

    # Load bot position from file
    def get_bot_position(self) -> Position:
        with open("./data.json", "r") as file:
            data = load(file)
            pos_data = data["bot_position"]
            return Position(pos_data["x"], pos_data["y"], pos_data["z"], pos_data["facing"])

    async def run_bot(self, room_id, api_key) -> None:
        asyncio.create_task(self.place_bot())
        definitions = [BotDefinition(self, room_id, api_key)]
        await __main__.main(definitions)

# Automatically create json file if not exists
def data_file(filename: str, default_data: str = "{}") -> None:
    if not os.path.exists(filename):
        with open(filename, 'w') as file:
            file.write(default_data)

DEFAULT_DATA = '{"users": {}, "bot_position": {"x": 0, "y": 0, "z": 0, "facing": "FrontRight"}}'
data_file("./data.json", DEFAULT_DATA)

if __name__ == "__main__":
    arun(Bot().run_bot(room_id, api_key))
```

`startbot.bat`
```bat
@echo off
title HighriseBot
python -m pip show highrise-bot-sdk >nul 2>&1
if errorlevel 1 (
    echo Highrise SDK not found. Installing...
    python -m pip install highrise-bot-sdk
) else (
    echo Starting bot...
)
:loop
python main.py
echo Waiting for 5 seconds before restarting...
timeout /t 5 /nobreak >nul
goto loop
```

But wait, there’s one more step before your bot can start! We need to let our script know the **secret token** attached to your bot, as well as which Highrise room you want your bot to join.

### Finding your unique Bot Token (API key)
First, go to the following link: [https://create.highrise.game/dashboard/credentials/api-keys](https://create.highrise.game/dashboard/credentials/api-keys)

![finding_bot_token.png](https://cdn-production.joinhighrise.com/create-portal/finding_bot_token_879a8915e5.png)

You will see your **Bots & API Keys** dashboard. If you haven’t created one already, click New Bot and set your Bot’s username.

Once created, click **‘Generate API Token’** and you will get a randomized key. Take note of that key and keep it safe, we’ll need it later.

### Finding your Highrise Room ID
Bots know which room to join using the unique **Room ID** each Highrise room has. The best way to get this ID is in-game, simply join your room, open up the room list, and tap **‘Share this Room’,** followed by** ‘Copy’.** Now you have an invite link to your room in your clipboard.

Paste that link anywhere, and you’ll see it looks like this: [https://high.rs/room?id=641b78a7ad0857b5099f55b6](https://high.rs/room?id=641b78a7ad0857b5099f55b6)

The link includes our unique Room ID at the end, in this case: **‘641b78a7ad0857b5099f55b6’**

Keep note of this **Room ID** along with your **Bot API Token**, now we need to put these in our script.

### Editing main.py with our information
Right click the **main.py** file and edit it with your editor of choice, by default Notepad is fine. You will see the following at the top of the script:

![editing_main_py.png](https://cdn-production.joinhighrise.com/create-portal/editing_main_py_f838d7a39d.png)

Go ahead and do what the comment says, filling in your **Room ID** between the quotation marks after **room_id = “”**, followed by the same for the **Bot Token** in the **api_key = “”** field. It should look roughly like this, except with your personal ID/token:

![editing_main_py2.png](https://cdn-production.joinhighrise.com/create-portal/editing_main_py2_a4fe7beeed.png)

Remember to save the file, then close your text editor, and we’re ready!

## Step 3: Start and use your bot

Simply click on the **startbot.bat** file to run your bot, this will automatically install what you need and if you followed these steps correctly you should now find your Bot inside your room! Note: Bots must have Designer permissions in a different player’s room to join.

This bot’s primary function is simply to accept tips from players, and allowing you to query the data for all tips - but first let’s move the bot from the doorway using our first command.

### !set - Set the bot position at your current location

![set-bot-position.jpeg](https://cdn-production.joinhighrise.com/create-portal/set_bot_position_6aa0b1755c.jpeg)

Upon using this command the bot will immediately teleport to your exact position, and then stay there forever! Even between disconnects and restarts. Place your bot in your ideal position where it will be visible for users to send tips and see its messages.

Now your bot is ready to be tipped. Encourage people at your parties/events to send tips directly to your bot. This gold goes directly to your bot’s wallet, which can be viewed on the create portal here: [https://create.highrise.game/dashboard/credentials/api-keys](https://create.highrise.game/dashboard/credentials/api-keys) - just click on any bot to see its current Gold/Earned Gold.

More commands:

### !top - See the top 10 tippers for your bot
![see-top-tippers.jpeg](https://cdn-production.joinhighrise.com/create-portal/see_top_tippers_e3096118d6.jpeg)
### !get `<player name>` - Find out how much `<player name>` has tipped
![see-wallet.jpeg](https://cdn-production.joinhighrise.com/create-portal/see_wallet_64c63ce3f9.jpeg)
### !wallet - Have the bot tell you how much gold it has in wallet

That’s it, you’re ready to use your bot to receive Earned Gold. If you ever need to change the room just follow the Room ID steps before. To stop your bot simply close the terminal, and to run your bot again just double click the startbot.bat file. Your PC must stay on for the bot to continue running - if you need a bot 24/7 inside your room you may have to look into hosting services online.

If you want to learn more about bots, their functionality, and coding, you can join the bot-api channel in the Highrise Discord. There’s plenty of resources and code snippets for you to look at and learn from, allowing your bot to do even more!