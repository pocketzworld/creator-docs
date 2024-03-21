# Games/Activities

### Blackjack Bot

![Blackjack (2).png](https://cdn-production.joinhighrise.com/create-portal/Blackjack_2_56994a55d8.png)

The Blackjack Bot is an interactive and engaging bot designed to facilitate a single lobby multiplayer blackjack game within your Highrise chat room. Using various chat-based commands, users can participate in a game of blackjack, making the Highrise experience more enjoyable and entertaining.

### **Usage:**

To begin playing blackjack with the bot, type the following command in the chat room where your bot is active to see the list of available commands:

```bash
/b help
```

Here are the other commands:

1. `/b create` - Create a blackjack game.
2. `/b start` - Start the blackjack game.
3. `/b join` - Join the blackjack game.
4. `/b lobby` - Show players in the blackjack game.
5. `/b hit` - Draw a card.
6. `/b stand` - End your turn.
7. `/b show` - Show the current cards on the table.
8. `/b quit` - Leave the blackjack game.
9. `/b yes` - Continue to play the next round.
10. `/b no` - Leave the blackjack game.

Here is the **[code](https://github.com/pocketzworld/example-bots/blob/main/blackjack/blackjack_bot.py)**:

```python
from highrise import BaseBot, User
from random import randrange

class BlackJackBot(BaseBot):
    """
    A Highrise bot implementing a simple multiplayer blackjack game through chat messages.

    This class extends the base Highrise bot and uses additional methods and states to implement
    a blackjack game in Highrise. The bot handles various commands and keeps track of the game state
    using the BlackJackGame class. 
    """

    identifier: str = "/b "  # Command prefix for the bot
    game: 'BlackJackGame' = None
    COMMANDS: list[str] = [
        "help",             # list all commands
        "create",           # create a blackjack game
        "start",            # start the blackjack game
        "join",             # join the blackjack game
        "lobby",            # show players in blackjack game
        "hit",              # draw a card
        "stand",            # end your turn
        "show",             # show the current cards on the table
        "quit",             # leave the blackjack game
        "yes",              # continue to play next round
        "no"                # leave the blackjack game
    ]
    COMMAND_REQUIREMENTS: dict[str, set[str]] = {
        "GAME_CREATED": {"start", "join", "lobby", "quit", "show", "hit", "stand", "yes", "no"},
        "GAME_START": {"show", "hit", "stand", "yes", "no"},
        "PLAYER_TURN": {"hit", "stand"}
    }
    COMMAND_INSTRUCTIONS: list[str] = [
        "help - list all commands",
        "create - create a blackjack game",
        "start - start the game",
        "join - join an already created game",
        "lobby - show who is in the current game",
        "hit - draw another card",
        "stand - end your turn",
        "show the current cards on the table",
        "quit - leave the game"
    ]

    async def on_user_leave(self, user: User) -> None:
        """On a user leaving the room."""
        if self.is_in_game(user):
            await self.game.remove_player(user)

    async def on_chat(self, user: User, message: str) -> None:
        """On a received room-wide chat."""
        message = message.lower()
        if (message.startswith(self.identifier)):
            await self.handle_command(user, message.removeprefix(self.identifier))

    async def handle_command(self, user: User, message: str) -> None:
        """Handler for all bot commands"""

        # Handle invalid commands
        if message in self.COMMAND_REQUIREMENTS["GAME_CREATED"] and not self.game_exists():
            return await self.whisper_to_user(user, "No game has been created")

        if message in self.COMMAND_REQUIREMENTS["GAME_START"] and not self.is_game_started():
            return await self.whisper_to_user(user, "No game has been started")

        if message in self.COMMAND_REQUIREMENTS["PLAYER_TURN"] and not self.is_current_player(user):
            return await self.whisper_to_user(user, "It is not your turn to play")

        # Handle bot commands
        match message:
            case 'create':
                if not self.game_exists():
                    self.game = BlackJackGame(self, user)
                    await self.highrise.chat("Created Blackjack game!")
                else:
                    await self.whisper_to_user(user, "A game has already been created")

            case 'start':
                if self.is_game_started():
                    await self.whisper_to_user(user, "The game has already started")
                elif not self.is_creator(user):
                    await self.whisper_to_user(user, "You are not the creator of this game")
                else:
                    await self.game.start_game()

            case 'join':
                if not self.is_in_game(user):
                    await self.game.add_player(user)
                else:
                    await self.whisper_to_user(user, "You are already in the game")

            case 'lobby':
                await self.show_lobby()

            case 'hit':
                await self.game.hit(user)

            case 'stand':
                await self.game.end_turn()

            case 'show':
                await self.game.show_table(False)

            case 'quit':
                if self.is_in_game(user):
                    await self.game.remove_player(user)
                else:
                    await self.whisper_to_user(user, "You are currently not in a game")

            case 'help':
                # a message in highrise is limited by 256 chars, so we have
                # to split the instructions into two groups
                await self.whisper_to_user(user, "\n" + "\n".join(self.COMMAND_INSTRUCTIONS[:3]))
                await self.whisper_to_user(user, "\n" + "\n".join(self.COMMAND_INSTRUCTIONS[3:]))

            case 'yes' | 'y':
                if self.is_creator(user):
                    await self.game.start_round()
                else:
                    await self.whisper_to_user(user, "You are not the creator of this game")

            case 'no' | 'n':
                await self.game.remove_player(user)

            case _:
                await self.whisper_to_user(user, f"Not a valid command. Use {self.identifier}help to see the list of commands")

    # HELPERS

    async def whisper_to_user(self, user: User, message: str) -> None:
        """Whispers a message to a user."""
        await self.highrise.send_whisper(user.id, message)

    async def show_lobby(self) -> None:
        """Display all players in the current game."""
        lines = ["lobby:"]
        for player in self.game.players:
            lines.append(player.username)
        await self.highrise.chat("\n".join(lines))

    async def end_game(self) -> None:
        """End the game."""
        lines = ["Game over!", f"Dealer wins: {self.game.dealer_wins}"]

        for player in self.game.players:
            lines.append(
                f"{player.username} wins: {self.game.player_wins[player.id]}")

        await self.highrise.chat("\n".join(lines))
        self.game = None

    def game_exists(self) -> bool:
        """Determines if game exists"""
        return hasattr(self, 'game') and self.game != None

    def is_in_game(self, user: User) -> bool:
        """Determines if user is in the current game"""
        if not self.game_exists():
            return False

        for player in self.game.players:
            if player.id == user.id:
                return True
        return False

    def is_current_player(self, user: User) -> bool:
        """Determines if it is the user's turn"""
        return self.is_in_game(user) and self.game.current_player < len(self.game.players) and self.game.players[self.game.current_player].id == user.id

    def is_game_started(self) -> bool:
        """Determines if game has started"""
        return self.game.is_started

    def is_creator(self, user: User) -> bool:
        """Determines if user is the creator of the game"""
        return self.game.creator.id == user.id

class BlackJackGame:
    """
    A class representing a blackjack game.

    This class keeps track of the game state, including the players, cards, and current turn.
    It handles various game actions such as starting the game, adding players, dealing cards,
    and managing player turns.
    """

    def __init__(self, bot: 'BlackJackBot', creator: User):
        self.bot: 'BlackJackBot' = bot
        self.creator: User = creator
        self.players: list[User] = [creator]
        self.deck: list[str] = self.create_deck()
        self.player_cards: dict[str, list[str]] = {creator.id: []}
        self.player_scores: dict[str, int] = {creator.id: []}
        self.dealer_cards: list[str] = []
        self.dealer_score: int = 0
        self.player_wins: dict[str, int] = {creator.id: 0}
        self.dealer_wins: int = 0
        self.current_player: int = 0
        self.round: int = 0
        self.is_started: bool = False

    def draw_card(self) -> str:
        """Returns and removes a card from the deck."""
        return self.deck.pop(randrange(len(self.deck)))

    def calculate_score(self, cards: list[str]) -> int:
        """Calculates the score of a hand in blackjack."""
        score = 0
        num_aces = 0
        for card in cards:
            if card.isdigit():
                score += int(card)
            elif card in ('J', 'Q', 'K'):
                score += 10
            elif card == 'A':
                num_aces += 1
                score += 11
        while score > 21 and num_aces > 0:
            score -= 10
            num_aces -= 1
        return score

    def create_deck(self) -> list[str]:
        """Creates a brand new 52 card deck."""
        return ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'K', 'Q'] * 4

    def deal_cards(self) -> None:
        """Deal cards to all players in the game."""
        for player in self.players:
            self.player_cards[player.id] = [self.draw_card(), self.draw_card()]
            self.player_scores[player.id] = self.calculate_score(
                self.player_cards[player.id])

        self.dealer_cards = [self.draw_card(), self.draw_card()]
        self.dealer_score = self.calculate_score(self.dealer_cards)

    async def show_table(self, reveal: bool = False) -> None:
        """Display the current table's cards."""
        lines = [f"Round: {self.round}"]
        for player in self.players:
            line = f"{player.username}: {' '.join(self.player_cards[player.id])}"
            if self.is_bust(player):
                line += " (bust)"
            elif self.current_player < len(self.players) and player.id == self.players[self.current_player].id:
                line += " (playing)"
            lines.append(line)

        # We need to hide the dealer's second card if the round is not over yet
        lines.append(
            f"Dealer: {self.dealer_cards[0]} {' '.join(self.dealer_cards[1:]) if reveal else '[X]'}")

        await self.bot.highrise.chat('\n'.join(lines))

    async def hit(self, user: User) -> None:
        """Give the player another card."""
        self.player_cards[user.id].append(self.draw_card())
        self.player_scores[user.id] = self.calculate_score(
            self.player_cards[user.id])
        await self.show_table()

        if self.is_bust(user):
            print(f"{user.username} has gone bust!")
            await self.end_turn()
        else:
            await self.bot.highrise.chat(f"{self.players[self.current_player].username}: Would you like to hit or stand?")

    async def end_turn(self) -> None:
        """End the player's turn."""
        self.current_player += 1
        if self.current_player >= len(self.players):
            await self.end_round()
        else:
            await self.show_table()
            await self.bot.highrise.chat(f"{self.players[self.current_player].username}: Would you like to hit or stand?")

    async def end_round(self) -> None:
        """End the current round."""
        await self.bot.highrise.chat("Dealer revealing...")

        # Dealer needs to draw cards until score >= 17
        while self.dealer_should_hit():
            self.dealer_cards.append(self.draw_card())
            self.dealer_score = self.calculate_score(self.dealer_cards)
        await self.show_table(True)

        if self.dealer_score > 21:
            # Dealer busts
            winners = []
            for p in self.players:
                if not self.is_bust(p):
                    self.player_wins[p.id] += 1
                    winners.append(p)

            # TODO: emote
            await self.bot.highrise.chat(f"Dealer has gone bust! {', '.join(p.username for p in winners)} win!")

        else:
            winners = [p for p in self.players if self.player_scores[p.id]
                       > self.dealer_score and not self.is_bust(p)]
            if len(winners) > 0:
                for player in winners:
                    # Update player wins count
                    self.player_wins[player.id] += 1

                await self.bot.highrise.chat(f"{', '.join(p.username for p in winners)} win!")
            else:
                # Dealer is the sole winner
                self.dealer_wins += 1
                # TODO: emote
                await self.bot.highrise.chat("Dealer wins!")  

        await self.bot.highrise.chat(f"{self.creator.username}, play another round? (yes/no)")

    async def start_round(self) -> None:
        """Start new blackjack round with new deck and deal cards to players."""
        self.round += 1
        self.deck = self.create_deck()
        self.deal_cards()
        self.current_player = 0

        await self.show_table()
        await self.bot.highrise.chat(f"{self.players[self.current_player].username}: Would you like to hit or stand?")

    def dealer_should_hit(self) -> None:
        """Determine if the dealer should hit."""
        if self.dealer_score < 17:
            return True
        if self.dealer_score == 17:
            for card in self.dealer_cards:
                if card == 'A':
                    return True
        return False

    def is_bust(self, user: User) -> bool:
        """Determines if player's hand is a bust."""
        return self.player_scores[user.id] > 21

    async def add_player(self, user: User) -> None:
        """Add a player to the game."""
        self.players.append(user)
        self.player_cards[user.id] = [self.draw_card(), self.draw_card()]
        self.player_scores[user.id] = self.calculate_score(
            self.player_cards[user.id])
        self.player_wins[user.id] = 0

        return await self.bot.highrise.chat(f"{user.username} has joined the game.")

    async def remove_player(self, user: User) -> None:
        """Remove a player from the game."""
        if (user.id == self.creator.id):
            # If the creator leaves, then end the game
            await self.bot.highrise.chat(f"{user.username} (Creator) has left the game.")
            await self.bot.end_game()
            return

        # Remove the player from all records
        for index, player in enumerate(self.players):
            if user.id == player.id:
                self.players = list(
                    filter(lambda x: x.id != user.id, self.players))
                del self.player_cards[user.id]
                del self.player_scores[user.id]
                del self.player_wins[user.id]

                if (index < self.current_player):
                    self.current_player -= 1

                await self.bot.highrise.chat(f"{user.username} has left the game.")

                if self.current_player >= len(self.players):
                    # End the round if the player was last to move
                    await self.end_round()
                return

    async def start_game(self) -> None:
        """Starts the game."""
        self.is_started = True
        await self.start_round()
```