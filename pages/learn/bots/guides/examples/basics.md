# Basics

### Echo Bot:

![Echo.png](https://cdn-production.joinhighrise.com/create-portal/Echo_07b9155d3c.png)

The Echo Bot serves as a foundational example for users looking to get started with creating Highrise bots. This basic yet effective bot prints out everything it sees in the chat room, providing a simple way to understand how bots interact with the Highrise environment.

As a beginner-friendly bot, the Echo Bot is capable of monitoring and displaying the following events to help users become familiar with bot functionalities:

1. User joining the room.
2. User leaving the room.
3. Hidden channel messages.
4. Start of the session.
5. Chat messages.
6. Whispers.
7. Received emotes.
8. User reactions.
9. Tips.
10. User movements.

Here is the **[code](https://github.com/pocketzworld/example-bots/blob/main/echo/echo_bot.py)**:

```python
from highrise import BaseBot, CurrencyItem, Item, Position, Reaction, SessionMetadata, User

class Bot(BaseBot):
    async def on_user_join(self, user: User, position: Position) -> None:
        """On a user joining the room."""
        print(f"[JOIN   ] {user.username}")

    async def on_user_leave(self, user: User) -> None:
        """On a user leaving the room."""
        print(f"[LEAVE  ] {user.username}")

    async def on_channel(self, sender_id: str, message: str, tags: set[str]) -> None:
        """On a hidden channel message."""
        pass

    async def on_start(self, session_metadata: SessionMetadata) -> None:
        print("[START  ]")

    async def on_chat(self, user: User, message: str) -> None:
        print(f"[CHAT   ] {user.username}: {message}")

    async def on_whisper(self, user: User, message: str) -> None:
        """On a whisper."""
        print(f"[WHISPER] {user.username} {message}")

    async def on_emote(self, user: User, emote_id: str, receiver: User | None) -> None:
        """On a received emote."""
        print(f"[EMOTE  ] {user.username} {emote_id} {receiver}")

    async def on_reaction(self, user: User, reaction: Reaction, receiver: User) -> None:
        """Called when someone reacts in the room."""
        print(f"[REACTION ] {user.username} {reaction} {receiver.username}")

    async def on_tip(
        self, sender: User, receiver: User, tip: CurrencyItem | Item
    ) -> None:
        """On a tip received in the room."""
        print(f"[TIP ] {sender.username} {receiver.username} {tip.type} {tip.amount}")

    async def on_user_move(self, user: User, pos: Position) -> None:
        """On a user moving in the room."""
        print(f"[MOVE ] {user.username} {pos.x} {pos.y} {pos.z}")
```
