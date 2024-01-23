# Third Party Integration

### Building a Weather Bot

![Weather.png](https://cdn-production.joinhighrise.com/create-portal/Weather_dadd073837.png)

This guide will walk you through the steps necessary to create a Highrise bot that provides real-time weather updates. Our Weather Bot will be able to read user commands from the chat room, make a request to a weather API, and display the requested weather information in the chat room.

### **Prerequisites:**

1. Python 3.11 or higher installed.
2. Highrise Python SDK installed
3. The **`httpx`** Python module installed. This module makes HTTP requests simpler and more human-friendly. Install it via pip by running **`pip install httpx`** in your terminal.
4. An API key from **[weatherapi.com](https://www.weatherapi.com/)**. This is necessary to access their weather data.

### **Step 1: Import Required Libraries**

The first step is to import the necessary libraries. 

```python
import httpx
from highrise import BaseBot, User
```

Here, `httpx` is a Python library used for making various types of HTTP requests such as GET and POST, and **`BaseBot`** and **`User`** are classes provided by the Highrise SDK

### **Step 2: Define the WeatherBot Class**

The next step is to define our **`WeatherBot`** class that extends the **`BaseBot`** class from the Highrise SDK. **`BaseBot`** is a base class for all bots that provides basic functionality like sending and receiving chat messages.

```python
class WeatherBot(BaseBot):
    """
    A Highrise bot that displays the current temperature based on location (city, country, etc.) input
    """
    identifier: str = "/w "  # Command prefix for the bot
    APIKEY: str = "<YOUR-API-KEY>" # API key for weatherapi.com
```

The **`WeatherBot`** class has two class attributes: **`identifier`** and **`APIKEY`**. **`identifier`** is the command prefix that the bot will respond to, and **`APIKEY`** is the weather API key that you obtained from [weatherapi.com](https://www.weatherapi.com/).

### **Step 3: Define the on_chat Method**

The **`on_chat`** method is an asynchronous method that will be called whenever a chat message is sent in the room.

The **`user`** parameter is an object of type **`User`** representing the user who sent the message, and **`message`** is a string containing the message text.

If the message starts with the **`identifier`**, the bot will treat the rest of the message as a command and pass it to the **`handle_command`** method. Python's **`str.startswith()`** method is used to check if the message starts with the identifier, and **`str.removeprefix()`** is used to remove the identifier from the message.

```python
    async def on_chat(self, user: User, message: str) -> None:
        """On a received room-wide chat."""
        if message.startswith(self.identifier):
            await self.handle_command(message.removeprefix(self.identifier))
```

Here, **`handle_command`** is a custom method we will define next to process commands from users.

### **Step 4: Define the handle_command Method**

The **`handle_command`** method is another asynchronous method that handles user commands. It first calls **`get_weather_data`** to retrieve the weather data, then formats and sends a response to the chat room.

```python
		async def handle_command(self, message: str) -> None:
		        """Handler for bot commands"""
		
		        response = await self.get_weather_data(message)
		
		        if response is not None:
		            # Convert the response to JSON format
		            data = response.json()
		            if "current" in data:
		                # Extract the current temperature and display it
		                await self.highrise.chat(f"The current temperature in {message} is:\n{data['current']['temp_c']} °C\n{data['current']['temp_f']} °F")
		            elif "error" in data:
		                # Common mistake is to forget to replace <YOUR-API-KEY>
		                await self.highrise.chat("Make sure you've configured your bot with a valid weatherapi.com API key")
		
		                # Other error handling would go here...
		
		            else:
		                # Handle unrecognized location
		                await self.highrise.chat(f"Unrecognized location: {message}")
		        else:
		            # Handle failed API request
		            await self.highrise.chat("Failed to retrieve weather data.")

```

The **`response`** object is a `httpx.Response` instance, which includes the server's response to an HTTP request. We check if the response is not **`None`**, then convert it into a JSON object using the **`.json()`** method. We check if the 'current' key is present in the data, which contains the current temperature. If it is, we send a message to the chat room with the temperature. If not, we send a message indicating that the location was not recognized. If the response was **`None`** (which means the API request failed), we send a message indicating the failure.

### **Step 5: Define the get_weather_data Method**

The **`get_weather_data`** method is utilized to make an asynchronous GET request to the weather API and fetch weather data for a specified location

```python
    async def get_weather_data(self, location: str) -> httpx.Response:
        """Retrieves and returns the weather data based on provided location"""
        async with httpx.AsyncClient() as client:
            # Send a GET request to the API endpoint
            response = await client.get(f"http://api.weatherapi.com/v1/current.json?key={self.APIKEY}&q={location}")

            return response

```

Within this function, we first construct the API request URL. This URL includes the base API endpoint, your API key, and the location specified by the user. We then use httpx's asynchronous client's **`get`** method to make a GET request to the API using the constructed URL. The response from the API is then returned by our **`get_weather_data`** function.

That's it! You've created a Weather Bot for Highrise. To use the bot, simply type **`/w <location>`** in the chat room where your bot is active. Replace **`<location>`** with your desired location, like **`/w Paris`**. Remember to replace **`<YOUR-API-KEY>`** in the **`APIKEY`** attribute of the **`WeatherBot`** class with your actual API key from weatherapi.com.

Please note that this bot is a basic implementation. You can extend its functionalities according to your requirements.

Here is the full **[code](https://github.com/pocketzworld/example-bots/blob/main/weather/weather_bot.py)**:

```python
import httpx
from highrise import BaseBot, User

"""
Note: 
Make sure you have the httpx module installed. You can install it using 'pip install httpx'.
An API key is also necessary to run this bot, sign up for a free one here: 'https://www.weatherapi.com/signup.aspx'

Usage:
To start interacting with the Weather Bot, use the following command in the chat of the 
room your bot is currently in, replacing <location> with the desired location:

/w <location>

Example:
/w Paris

The Weather Bot will provide you with the current temperature for the specified location.

Please note that the accuracy and availability of weather data may vary depending on the location and the weather API being used.
"""

class WeatherBot(BaseBot):
    """
    A Highrise bot that displays the current temperature based on location (city, country, etc.) input

    This class extends the base Highrise bot and uses a third-party API to retrieve weather information. It 
    offers a command to retrieve the temperature of a specified location in celsius and fahrenheit. 
    """

    identifier: str = "/w "  # Command prefix for the bot
    APIKEY: str = "<YOUR-API-KEY>" # API key for weatherapi.com 

    async def on_chat(self, user: User, message: str) -> None:
        """On a received room-wide chat."""

        # Handle commands
        if message.startswith(self.identifier):
            await self.handle_command(message.removeprefix(self.identifier))

    async def handle_command(self, message: str) -> None:
        """Handler for bot commands"""

        response = await self.get_weather_data(message)

        if response is not None:
            # Convert the response to JSON format
            data = response.json()
            if "current" in data:
                # Extract the current temperature and display it
                await self.highrise.chat(f"The current temperature in {message} is:\n{data['current']['temp_c']} °C\n{data['current']['temp_f']} °F")
            elif "error" in data:
                # Common mistake is to forget to replace <YOUR-API-KEY>
                await self.highrise.chat("Make sure you've configured your bot with a valid weatherapi.com API key")

                # Other error handling would go here...

            else:
                # Handle unrecognized location
                await self.highrise.chat(f"Unrecognized location: {message}")
        else:
            # Handle failed API request
            await self.highrise.chat("Failed to retrieve weather data.")

    async def get_weather_data(self, location: str) -> httpx.Response:
        """Retrieves and returns the weather data based on provided location"""
        async with httpx.AsyncClient() as client:
            # Send a GET request to the API endpoint
            response = await client.get(f"http://api.weatherapi.com/v1/current.json?key={self.APIKEY}&q={location}")

            return response
```