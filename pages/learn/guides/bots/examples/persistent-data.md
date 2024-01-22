# Persistent Data

### Building a Statistics Bot

![Statistics.png](https://cdn-production.joinhighrise.com/create-portal/Statistics_dbe0420d4c.png)

This guide provides a detailed, step-by-step walkthrough of the implementation of the Statistics Bot. The Statistics Bot is a bot for the Highrise platform that tracks and reports user activity. It also features a leaderboard for the most active users.

### **Prerequisites:**

1. Python 3.11 or higher installed.
2. Highrise Python SDK installed
3. Make sure that an empty **`data.json`** file exists in the same directory as your bot file. This file will be used to store user activity data in JSON format. You can create it with the following content:

```json
{
}
```

### **Step 1: Import Required Libraries**

The first step in creating the Statistics Bot is to import the necessary libraries. These libraries provide the functions and classes we need to interact with Highrise and perform calculations.

```python
from json import load, dump
from time import time
from math import sqrt
from highrise import BaseBot, User, Position, AnchorPosition
```

Here's what each import is for:

- **`json`**: This module is used to work with JSON data.
- **`time`**: This module is used to get the current time, which helps in calculating the time spent by a user in the room.
- **`sqrt`**: This function from the **`math`** module is used to calculate the distance a user travels in the room.
- **`BaseBot, User, Position, AnchorPosition`**: These classes from the **`highrise`** module are used to interact with the Highrise platform.

## **3. Defining the StatisticsBot Class**

Next, we define the **`StatisticsBot`** class, which extends the **`BaseBot`** class from the Highrise library. This class will contain all the functionality for our bot.

```python
class StatisticsBot(BaseBot):
    identifier: str = "/s "  # Command prefix for the bot
    lobby: Dict[str, dict] = {}  # A dictionary to store user activity data temporarily

```

We define two class variables: **`identifier`** and **`lobby`**. **`identifier`** is the command prefix that users will use to interact with the bot. **`lobby`** is a dictionary that will temporarily store user data while they are in the room.

## **4. Implementing Event Handlers**

We override several event handlers from the **`BaseBot`** class to track user activity in the room. These handlers respond to events such as users joining the room, leaving the room, moving within the room, and sending chat message

### **4.1 on_chat Event Handler**

The **`on_chat`** method is called whenever a user sends a chat message in the room. Here, we perform two tasks: we update the total number of characters the user has sent in chat messages, and we check if the message is a command for our bot.

```python
    async def on_chat(self, user: User, message: str) -> None:
        num_chars = len(message)
        self.write_data(user, "chat_message_chars", num_chars)

        if (message.startswith(self.identifier)):
            await self.handle_command(user, message.removeprefix(self.identifier))
```

In this method, **`num_chars`** is the number of characters in the chat message. We then call **`write_data`** to update the user's total chat message characters in the **`data.json`** file (which we will define later). Finally, we check if the message starts with our bot's command prefix (**`/s`** ), and if it does, we call **`handle_command`** to process the command.

### **4.2 on_user_join Event Handler**

The **`on_user_join`** method is called whenever a user joins the room. In this method, we add the user to our **`lobby`** dictionary with a default data set if they are not already in it.

```python
    async def on_user_join(self, user: User) -> None:
        if not user.id in self.lobby:
            self.lobby[user.id] = self.create_default()
```

### **4.3 on_user_leave Event Handler**

The **`on_user_leave`** method is called whenever a user leaves the room. Here, we calculate the total time the user spent in the room, update this in the **`data.json`** file, and then remove the user from our **`lobby`** dictionary.

```python
   async def on_user_leave(self, user: User) -> None:
        if user.id in self.lobby:
            time_spent = round(time() - self.lobby[user.id]["time_joined"])
            self.write_data(user, "time_spent", time_spent)
            del self.lobby[user.id]
```

### **4.4 on_user_move Event Handler**

The **`on_user_move`** method is called whenever a user moves within the room. We use this method to track the distance the user travels. If the user's position is of type **`Position`**, we calculate the distance between their new position and their last position, update this in the **`data.json`** file, and then update their last position in our **`lobby`** dictionary.

```python
    async def on_user_move(self, user: User, pos: Position | AnchorPosition) -> None:
        if isinstance(pos, Position):
            if not user.id in self.lobby:
                self.lobby[user.id] = self.create_default()
            distance = self.calculate_distance(self.lobby[user.id]["last_pos"], pos)
            self.write_data(user, "distance_travelled", distance)
            self.lobby[user.id]["last_pos"] = pos
```

## **5. Implementing Helper Methods**

Several helper methods are used to perform various tasks such as writing data to the JSON file, handling bot commands, calculating the distance a user has traveled, and generating the leaderboard.

### **5.1 write_data Helper Method**

The **`write_data`** method is used to write user activity data to the **`data.json`** file. It takes as arguments the user, the key of the data (e.g., "time_spent"), and the value of the data.

```python
    def write_data(self, user: User, key: str, value: int) -> None:
        with open("./data.json", "r+") as file:
            data = load(file)
            file.seek(0)
            if user.id in data:
                data[user.id][key] = data[user.id][key] + value
            else:
                data[user.id] = {
                    "time_spent": 0,
                    "chat_message_chars": 0,
                    "distance_travelled": 0,
                    "username": user.username
                }
                data[user.id][key] = value
            print(f"Updated {user.username} with {value} of {key}")
            dump(data, file)
            file.truncate()
```

(Ideally, reading and writing to the file system should be done asynchronously, with a library like [aiofiles](https://github.com/Tinche/aiofiles))

### **5.2 handle_command Helper Method**

The **`handle_command`** method is used to process the commands sent by users in the chat. It takes as arguments the user and the message (without the command prefix).

```python
    async def handle_command(self, user: User, message: str) -> None:
        match message:
            case "leaderboard":
                with open("./data.json", "r") as file:
                    data = load(file)
                    top_five = self.get_leaderboard(data)
                    await self.highrise.chat("Leaderboard:\n" + "\n".join(top_five))
						case username if message.startswith("@") and len(message[1:]) > 0:
						         with open("./data.json", "r") as file:
						             data = load(file)
						             username = username[1:]
						             for value in data.values():
						                 if value["username"] == username:
						                     stats = [
						                         f"Distance Walked: {value['distance_travelled']}",
						                         f"Time Spent: {value['time_spent']}",
						                         f"Characters Messaged: {value['chat_message_chars']}"
						                     ]
						                     return await self.highrise.chat(f"{username}:\n" + "\n".join(stats))
						             return await self.highrise.chat(f"{username} does not exist or has not joined this room before")
						
						     case _:
						         await self.highrise.send_whisper(user.id, f"Not a valid command. Use {self.identifier}help to see the list of commands")
```

This method supports two commands: `/s leaderboard` to generate a leaderboard of the top five most active users, and `/s @<username>` to display activity metrics for the specified user.

### 5.3 calculate_distance Helper Method

The `calculate_distance` method is used to calculate the distance a user has traveled based on their last and next positions.

```python
    def calculate_distance(self, lastpos: Position, nextpos: Position) -> None:
        return round(sqrt(pow(lastpos.x - nextpos.x, 2) + pow(lastpos.y - nextpos.y, 2) + pow(lastpos.z - nextpos.z, 2)))
```

This completes the implementation of the Statistics Bot. To use the bot, simply type **`/s leaderboard`** or `/s @<Myusername>` in the chat room where your bot is active. Replace `<Myusername>` with your desired username. 

Here is the full [code](https://github.com/pocketzworld/example-bots/blob/main/statistics/statistics_bot.py):

```python
from json import load, dump
from time import time
from math import sqrt
from highrise import BaseBot, User, Position, AnchorPosition

"""
Note:
Make sure there exists an empty data.json file in the directory of the bot file.

Usage:
To start interacting with the statistics bot, use any of the following commands in the chat of the 
room your bot is currently in to see statistics of users who have entered your room:

/s leaderboard
/s @<username>

Example:
/s @Myusername

The Statistics Bot will provide you with activity metrics for the specified user. 
"""

class StatisticsBot(BaseBot):
    """
    A Highrise bot that passively tracks user activity in a room.

    This class extends the base Highrise bot and uses a local JSON file to record
    user activity. It offers commands to view specific users' activity, along with
    a leaderboard of the most active users in the room. 
    """

    identifier: str = "/s "  # Command prefix for the bot
    lobby: dict[str, dict] = {} # A dictionary to store user activity data temporarily

    async def on_chat(self, user: User, message: str) -> None:
        """On a received room-wide chat."""

        # Calculate the number of characters in the message
        num_chars = len(message)

        # Write the data to JSON
        self.write_data(user, "chat_message_chars", num_chars)

        # Handle commands
        if message.startswith(self.identifier):
            await self.handle_command(user, message.removeprefix(self.identifier))

    async def on_user_join(self, user: User) -> None:
        """On a user joining the room."""

        if not user.id in self.lobby:
            # Add the user to the lobby
            self.lobby[user.id] = self.create_default()

    async def on_user_leave(self, user: User) -> None:
        """On a user leaving the room."""

        if user.id in self.lobby:
            # Calculate the number of seconds the user spent in the room
            time_spent = round(
                time() - self.lobby[user.id]["time_joined"])

            # Write the data to JSON
            self.write_data(user, "time_spent", time_spent)

            # Remove the user's entry from the lobby
            del self.lobby[user.id]

    async def on_user_move(self, user: User, pos: Position | AnchorPosition) -> None:
        """On a user moving in the room."""

        # We're only tracking distance for Position, not AnchorPosition
        if isinstance(pos, Position):
            if not user.id in self.lobby:
                self.lobby[user.id] = self.create_default()

            # Calculate the distance
            distance = self.calculate_distance(
                self.lobby[user.id]["last_pos"], pos)

            # Write the data to JSON
            self.write_data(user, "distance_travelled", distance)

            # Set their new "last_pos"
            self.lobby[user.id]["last_pos"] = pos

    def write_data(self, user: User, key: str, value: int) -> None:
        """Writes data to local JSON file"""

        with open("./data.json", "r+") as file:
            data = load(file)

            # Move the file pointer back to the beginning
            file.seek(0)

            # Perform desired operations on the data
            if user.id in data:
                data[user.id][key] = data[user.id][key] + value
            else:
                # New user in the room
                data[user.id] = {
                    "time_spent": 0,
                    "chat_message_chars": 0,
                    "distance_travelled": 0,
                    "username": user.username
                }
                data[user.id][key] = value

            # Print the updated data
            print(f"Updated {user.username} with {value} of {key}")

            # Write the updated data back to the file
            dump(data, file)
            file.truncate()

    async def handle_command(self, user: User, message: str) -> None:
        """Handler for all bot commands"""

        match message:
            case "leaderboard" | "Leaderboard":
                with open("./data.json", "r") as file:
                    data = load(file)

                    # Get the top 5 most active users by score
                    top_five = self.get_leaderboard(data)
                    await self.highrise.chat("Leaderboard:\n" + "\n".join(top_five))

            case username if message.startswith("@") and len(message[1:]) > 0:
                with open("./data.json", "r") as file:
                    data = load(file)

                    username = username[1:]  # trim @ character

                    for value in data.values():
                        if value["username"] == username:
                            stats = [
                                f"Distance Walked: {value['distance_travelled']}",
                                f"Time Spent: {value['time_spent']}",
                                f"Characters Messaged: {value['chat_message_chars']}"
                            ]
                            return await self.highrise.chat(f"{username}:\n" + "\n".join(stats))

                    # User does not exist in our JSON
                    return await self.highrise.chat(f"{username} does not exist or has not joined this room before")
            case _:
                await self.highrise.send_whisper(user.id, f"Not a valid command. Use {self.identifier}help to see the list of commands")

    def calculate_distance(self, lastpos: Position, nextpos: Position) -> None:
        """Calculate the distance a user has travelled based on their last and next locations"""
        return round(sqrt(pow(lastpos.x - nextpos.x, 2) + pow(lastpos.y - nextpos.y, 2) + pow(lastpos.z - nextpos.z, 2)))

    def create_default(self) -> dict[str, object]:
        """Create a dictionary to track user data"""
        return ({
                "last_pos": Position(0, 0, 0, "FrontRight"),
                "time_joined": time()
                })

    def get_leaderboard(self, data: dict[str, dict]) -> list[str]:
        """Returns the top 5 most active users based on their score, where the score is the sum of all metrics"""

        # Calculate the score for each user
        scores = {metrics["username"]: self.calculate_score(
            metrics) for metrics in data.values()}

        # Sort the users based on their scores in descending order
        sorted_users = sorted(scores, key=scores.get, reverse=True)

        # Get the top 5 users
        top_five = sorted_users[:5]

        return top_five

    def calculate_score(self, data: dict[str, dict]) -> list[str]:
        """Calculates the score of a user to determine leaderboard rankings"""
        return data["time_spent"] + data["chat_message_chars"] + data["distance_travelled"]
```