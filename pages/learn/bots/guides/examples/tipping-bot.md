## Building a Tipping Bot

![Tipping Bot](https://cdn-production.joinhighrise.com/create-portal/Tipping_Bot_8180d7633b.png)

This guide will walk you through the steps necessary to create a Highrise Tipping bot that allows room administrators to monitor, acknowledge, and provide insights into tipping activities within a Highrise room. This bot responds to tipping events, logs user tipping data, and offers commands to query and display this data. Special shoutout to our Highrise Builder @AprilCat for creating this bot!

**Prerequisites:**

1. Python 3.11 or higher installed.
2. Highrise Python SDK installed
3. Make sure that an empty **`tip-data.json`** file exists in the same directory as your bot file. This file will be used to store tipping data in JSON format.

**Step 1: Import Libraries and Constants**

Before diving into the code, ensure you have the necessary libraries and constants ready.

```python
from typing import Optional, Dict, Union
from json import load, dump
from highrise import BaseBot, User, CurrencyItem, Item, SessionMetadata
```

We also set a constant **`FILE_PATH`** that points to the path of the JSON data file.

```python
FILE_PATH = "./tip-data.json"
```

**Step 2: Define the TippingBot Class**

Next, we'll define the main **`TippingBot`** class. During initialization, the bot loads existing tipping data and sets up some default properties. We’ve also defined the `on_start` handler to initialize some default ids. 

```python
class TippingBot(BaseBot):
    def __init__(self):
        self.bot_id = None
        self.owner_id = None
        self.tip_data: Dict[str, Dict[str, Union[str, int]]] = {}
        self.load_tip_data()

		async def on_start(self, session_metadata: SessionMetadata) -> None:
	    print("Bot Connected")
	    self.bot_id = session_metadata.user_id
	    self.owner_id = session_metadata.room_info.owner_id
```

**Step 3: Handle Different Message Types**

The bot is designed to handle three types of messages: chat, whisper, and direct messages.

```python
async def on_chat(self, user: User, message: str) -> None:
		await self.process_message(self.highrise.chat, message, user, "Chat Error")

async def on_whisper(self, user: User, message: str) -> None:
    await self.process_message(
        self.highrise.send_whisper, message, user, "Whisper Error", user.id
    )

async def on_message(
    self, user_id: str, conversation_id: str, is_new_conversation: bool
) -> None:
    conversation = await self.highrise.get_messages(conversation_id)
    message = conversation.messages[0].content
    await self.process_message(
        self.highrise.send_message, message, user_id=user_id, error_message="Message Error", conversation_id=conversation_id
    )
```

**Step 4: Process Messages**

All message types are processed by a common method which triggers a command handler.

```python
async def process_message(self, method, message: str, user=None, error_message: str = "", *args):
    response = await self.command_handler(user.id if user else None, message)
    if response:
        try:
            await method(response, *args)
        except Exception as e:
            print(f"{error_message}: {e}")
```

**Step 5: Handle Tips**

The bot listens for tips, logs/saves relevant data, and acknowledges generous contributions.

```python
async def on_tip(self, sender: User, receiver: User, tip: Union[CurrencyItem, Item]) -> None:
    if receiver.id != self.bot_id:
        return

    if isinstance(tip, CurrencyItem):
        print(f"{sender.username} tipped {tip.amount}g -> {receiver.username}")
        self.update_tip_data(sender, tip.amount)
        if tip.amount >= 500:
            await self.highrise.chat(f"Thank you {sender.username} for the generous {tip.amount}g tip!")

def update_tip_data(self, user: User, tip: int) -> None:
    user_data = self.tip_data.get(user.id, {"total_tips": 0, "username": user.username})
    user_data["total_tips"] += tip
    user_data["username"] = user.username
    self.tip_data[user.id] = user_data
    self.save_tip_data()
```

**Step 6: Command Handler**

The command handler processes owner commands, such as viewing top tippers or querying a specific user's tip amount.

```python
async def command_handler(self, user_id: Optional[str], message: str) -> Optional[str]:
    if user_id != self.owner_id:
        return None

    command = message.lower().strip()
    if command == "!top":
        return self.build_top_tippers_message()
    elif command.startswith("!get "):
        username = command.split(" ", 1)[1].replace("@", "")
        return self.get_user_tip_message(username)
```

**Step 7: Utility Functions**

Various utility functions help build messages, retrieve tip amounts, and manage the tipping data.

```python
def build_top_tippers_message(self) -> str:
    top_tippers = self.get_top_tippers()
    formatted_tippers = [f"{i + 1}. {user_data['username']} ({user_data['total_tips']}g)" for i, user_data in enumerate(top_tippers)]
    separator = "\n"
    return f"Top Tippers:\n{separator.join(formatted_tippers)}"

def get_user_tip_message(self, username: str) -> str:
    tip_amount = self.get_user_tip_amount(username)
    if tip_amount is not None:
        return f"{username} has tipped {tip_amount}g"
    else:
        return f"{username} hasn't tipped."

def get_top_tippers(self) -> list:
    return sorted(self.tip_data.values(), key=lambda x: x["total_tips"], reverse=True)[:10]

def get_user_tip_amount(self, username: str) -> Optional[int]:
    for user_data in self.tip_data.values():
        if user_data["username"].lower() == username.lower():
            return user_data["total_tips"]

```

**Step 8: Data Management**

The bot reads and writes tipping data to a local JSON file for persistence.

```python
def load_tip_data(self) -> None:
    try:
        with open(FILE_PATH, "r") as file:
            self.tip_data = load(file)
    except FileNotFoundError:
        self.tip_data = {}

def save_tip_data(self) -> None:
    with open(FILE_PATH, "w") as file:
        dump(self.tip_data, file)
```

---

Congratulations! You've now created a Tipping Bot for Highrise. This bot acknowledges generous tippers and provides a way for the room owner to view the top tippers or query the tipping history of specific users. 

Here is the full code:

```python
from typing import Optional, Dict, Union
from json import load, dump
from highrise import BaseBot, User, CurrencyItem, Item, SessionMetadata

FILE_PATH = "./tip-data.json"

class TippingBot(BaseBot):
    def __init__(self):
        self.bot_id = None
        self.owner_id = None
        self.tip_data: Dict[str, Dict[str, Union[str, int]]] = {}
        self.load_tip_data()

    async def on_start(self, session_metadata: SessionMetadata) -> None:
        print("Bot Connected")
        self.bot_id = session_metadata.user_id
        self.owner_id = session_metadata.room_info.owner_id

    async def on_chat(self, user: User, message: str) -> None:
            await self.process_message(self.highrise.chat, message, user, "Chat Error")

    async def on_whisper(self, user: User, message: str) -> None:
        await self.process_message(
            self.highrise.send_whisper, message, user, "Whisper Error", user.id
        )

    async def on_message(
        self, user_id: str, conversation_id: str, is_new_conversation: bool
    ) -> None:
        conversation = await self.highrise.get_messages(conversation_id)
        message = conversation.messages[0].content
        await self.process_message(
            self.highrise.send_message, message, user_id=user_id, error_message="Message Error", conversation_id=conversation_id
        )
        
    async def process_message(self, method, message: str, user=None, error_message: str = "", *args):
        response = await self.command_handler(user.id if user else None, message)
        if response:
            try:
                await method(response, *args)
            except Exception as e:
                print(f"{error_message}: {e}")

    async def on_tip(self, sender: User, receiver: User, tip: Union[CurrencyItem, Item]) -> None:
        if receiver.id != self.bot_id:
            return

        if isinstance(tip, CurrencyItem):
            print(f"{sender.username} tipped {tip.amount}g -> {receiver.username}")
            self.update_tip_data(sender, tip.amount)
            if tip.amount >= 500:
                await self.highrise.chat(f"Thank you {sender.username} for the generous {tip.amount}g tip!")

    def update_tip_data(self, user: User, tip: int) -> None:
        user_data = self.tip_data.get(user.id, {"total_tips": 0, "username": user.username})
        user_data["total_tips"] += tip
        user_data["username"] = user.username
        self.tip_data[user.id] = user_data
        self.save_tip_data()
    
    async def command_handler(self, user_id: Optional[str], message: str) -> Optional[str]:
        if user_id != self.owner_id:
            return None

        command = message.lower().strip()
        if command == "!top":
            return self.build_top_tippers_message()
        elif command.startswith("!get "):
            username = command.split(" ", 1)[1].replace("@", "")
            return self.get_user_tip_message(username)
    
    def build_top_tippers_message(self) -> str:
        top_tippers = self.get_top_tippers()
        formatted_tippers = [f"{i + 1}. {user_data['username']} ({user_data['total_tips']}g)" for i, user_data in enumerate(top_tippers)]
        separator = "\n"
        return f"Top Tippers:\n{separator.join(formatted_tippers)}"

    def get_user_tip_message(self, username: str) -> str:
        tip_amount = self.get_user_tip_amount(username)
        if tip_amount is not None:
            return f"{username} has tipped {tip_amount}g"
        else:
            return f"{username} hasn't tipped."

    def get_top_tippers(self) -> list:
        return sorted(self.tip_data.values(), key=lambda x: x["total_tips"], reverse=True)[:10]

    def get_user_tip_amount(self, username: str) -> Optional[int]:
        for user_data in self.tip_data.values():
            if user_data["username"].lower() == username.lower():
                return user_data["total_tips"]

    def load_tip_data(self) -> None:
        try:
            with open(FILE_PATH, "r") as file:
                self.tip_data = load(file)
        except FileNotFoundError:
            self.tip_data = {}

    def save_tip_data(self) -> None:
        with open(FILE_PATH, "w") as file:
            dump(self.tip_data, file)
```