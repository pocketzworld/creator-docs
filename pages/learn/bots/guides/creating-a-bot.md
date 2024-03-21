# Creating a Bot with the Python SDK 

## Introduction

The Highrise Bot API is a tool for developers to access and manipulate the Highrise virtual world. It allows for the creation of virtual objects, avatars, and interactions within the world, as well as the ability to track user behavior and data. With the API, developers can build custom experiences and applications within Highrise. It is a powerful tool that can be used for a wide range of purposes, from gaming and social networking to education and training.

There are multiple ways to interact with the Highrise API. The first of which is a direct connection to the API via a web socket. This method allows you direct access to the JSON payloads coming in and out and you can use whatever programming language you prefer. Alternatively, we’ve also provided a Python SDK that will take care of all the plumbing and setup necessary and enable access to the API via structured data and functions. Both methods are equivalent and you’re welcome to choose either. 

# Credentials

## API Token

Go to [https://create.highrise.game](https://create.highrise.game), log in with the user you intend to be the owner of your bot, go to *Dashboard,* then *Bots & API Keys*, and create a new bot. Once a new bot has been created, you can click on the generate API Token button to generate a new bot API token. This will act as the identifier for your bot, and you will use this when connecting your bot.

![credentials.png](https://cdn-production.joinhighrise.com/create-portal/credentials_6ae6e5f186.png)

## Room ID

Next, you’ll need to retrieve the ID of the room you want to send the bot to. To do so, you can visit the room in the Highrise App, navigate to the room info panel on the top right and select "Share this Room". This will generate a link that contains the ID of the room. You'll be able to use this ID in your API/SDK calls to send the bot to that room.

<Note>
    Bots need designer rights to the room they’re entering
</Note>

![Room ID](https://cdn-production.joinhighrise.com/create-portal/room_ID_a5a157d527.jpg)

## Subscribing to Events
By default bots will receive all events that occur in the room they are deployed to. This can be a lot of data, and you may only be interested in a subset of events. To subscribe to specific events you can send optional query parameter events while connecting to websocket. The value of this parameter should be a comma separated with list of all events you want to subscribe to. For example, if you only want to receive chat messages and avatar joined events, you can send the following query parameter: `?events=chat,user_joined`. The full list of events can be found in the API documentation below.

### List of possible events
Note that chat covers both chat and whisper events.
 - chat
 - emote
 - reaction
 - user_joined
 - user_left
 - user_moved
 - tip_reaction
 - voice
 - channel

# Python SDK

The Python SDK is designed to be an easy way to get started with using the Highrise API. The SDK includes all the necessary plumbing code to connect to the Highrise backend and exposes all the API endpoints in easy to use python function calls.

Releases: [https://pypi.org/project/highrise-bot-sdk/](https://pypi.org/project/highrise-bot-sdk/)

## Getting Started

For Windows setup, please follow this [guide](https://create.highrise.game/learn/guides/bots/local/windows).

For Mac setup, please follow this [guide](https://create.highrise.game/learn/guides/bots/local/mac).