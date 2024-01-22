# Understanding Bot Outfits in Highrise

A bot's outfit within Highrise is a list of items the bot can submit to the API to alter its appearance. For an outfit to be valid and accepted by the API, certain requirements must be met. The bot must either use free items, which will be discussed later, or have at least one replica of the item in their inventory. Let's delve deeper into these concepts:

### Inventory

Every Highrise user, including bots, has a main inventory. Although human users might store a variety of items like furniture and collectibles, bots can only access avatar items, which are essentially game items denoted by the type "clothing". When discussing bots, any reference to inventory pertains strictly to "clothing" items.

Bots can fetch their inventory using the `GetInventoryRequest()` function or `self.highrise.get_inventory()` if using the Python SDK. Here's a part of a typical inventory response:

```python
...
Item(
    type='clothing',
    amount=1,
    id='shirt-n_room32019denimjackethoodie',
    account_bound=False,
    active_palette=None
),
Item(
    type='clothing',
    amount=1,
    id='pants-n_starteritems2019cuffedjeanswhite',
    account_bound=False,
    active_palette=None
),
Item(
    type='clothing',
    amount=1,
    id='shoes-n_room32019socksneakersgrey',
    account_bound=False,
    active_palette=None
),
...
```
This inventory snippet signifies the default items a user has—in this case, a shirt, pants, and shoes. Note that the `account_bound` parameter marks items limited to the bot account and untradeable. While trading isn't relevant to bots, it's crucial when equipping items. Lastly, the `active_palette` is always `None` in inventory responses, as it's not tracked in the inventory.

### Outfits

An outfit is essentially a list of items the bot currently wears, reflecting the user's avatar look. It's important to note that changing an outfit follows certain guidelines; if not followed, the server rejects it. Once an outfit is set up satisfactorily, it satisfies the minimal conditions necessary for an outfit. 

As an illustration, let's look at a typical `GetUserOutfitResponse` that a bot may be initialized with:

```python
GetUserOutfitResponse(
    outfit=[
        Item(
            type='clothing',
            amount=1,
            id='hair_front-n_malenew05',
            account_bound=False,
            active_palette=1
        ),
        Item(
            type='clothing',
            amount=1,
            id='hair_back-n_malenew05',
            account_bound=False,
            active_palette=1
        ),
        Item(
            type='clothing',
            amount=1,
            id='body-flesh',
            account_bound=False,
            active_palette=27
        ),
        Item(
            type='clothing',
            amount=1,
            id='eye-n_basic2018malesquaresleepy',
            account_bound=False,
            active_palette=7
        ),
        Item(
            type='clothing',
            amount=1,
            id='eyebrow-n_basic2018newbrows07',
            account_bound=False,
            active_palette=0
        ),
        Item(
            type='clothing',
            amount=1,
            id='nose-n_basic2018newnose05',
            account_bound=False,
            active_palette=0
        ),
        Item(
            type='clothing',
            amount=1,
            id='mouth-basic2018chippermouth',
            account_bound=False,
            active_palette=-1
        ),
        Item(
            type='clothing',
            amount=1,
            id='freckle-n_basic2018freckle04',
            account_bound=False,
            active_palette=0
        ),
        Item(
            type='clothing',
            amount=1,
            id='shirt-n_room32019denimjackethoodie',
            account_bound=False,
            active_palette=0
        ),
        Item(
            type='clothing',
            amount=1,
            id='pants-n_starteritems2019cuffedjeanswhite',
            account_bound=False,
            active_palette=0
        ),
        Item(
            type='clothing',
            amount=1,
            id='shoes-n_room32019socksneakersgrey',
            account_bound=False,
            active_palette=0
        )
    ],
    rid='0'
)
```

The outfit must contain items from specific categories:

1. Bot's outfit should always include the "body-flesh" item within the `set_outfit` requests. Note that the skin tone can be changed using `active_palette`, with the default being set to `27`.
2. Other categories you need to include in your outfit request are "eye", "eyebrow", "nose", and "mouth".
3. Lastly, you'll need a combination of either a "shirt" and "pants", a "shirt" and  "skirt", a "dress", or a "fullsuit". 

Failure to include these items will lead to rejection by the server as this forms the minimum outfit requirements. To customize your bot's appearance, it's recommended to start with the default outfit obtained using the `get_my_outfit()` method and swap items as needed. 

Remember that these basic types can only be equipped once, so they should only be submitted once in the outfit request. If you attempt to set an outfit with two "mouth" category items, for instance, the server would reject it. 

The process provides plenty of room for personalizing your bot's avatar within the constraints of the item requirements. Such a structure helps maintain consistency and quality of user avatars across the platform. 

When you understand how outfit works, you can use it to give your bot's avatar a unique and appealing look that complements its purpose and function in the game.

### How to Equip Items

Equipping items to a bot's avatar is an essential part of defining its appearance. When a bot is first created in Highrise, it is populated with a default outfit. This outfit is combined with default inventory items which are automatically generated for the bot.

In order to set new outfit for a bot, a `SetOutfitRequest(outfit)` call can be used, in this case outfit is a list of items just like we described in outfit section.

A bot can equip any item in its inventory. These items can be fetched and managed using the `GetInventoryRequest` function or `self.highrise.get_inventory` if you're using the Python SDK. However, remember that the nature of bot outfits means they can only access "clothing" items.

For a bot to equip a new item, it has to own at least one copy of that item in its inventory. The bot can equip these items by referencing the item's unique ID when making a GetInventoryRequest.

Bots can also equip any free items. Free items can be identified with the attribute `rarity=none` in the items API (https://webapi.highrise.game/items?rarity=none).

An interesting aspect of the bot's outfit capabilities is the ability to purchase items from the Highrise store. A bot can buy a new item that's available in the store for gold, by using the `buy_item("item_id")` function or the `BuyItemRequest` API call. Remember that the bot can only purchase items that are directly purchasable with gold from the shop—items in grabs or item collections are off-limits.

Once a bot has an item in its inventory, be it a default item, a free item, or a purchased one, it can equip the item by including the item in an outfit request—an API call that sets the bot's current outfit. 

It's critical to understand that while a bot can have multiple copies of the same item in its inventory, each item can only be equipped once. Even if a bot has multiple copies of an item, it will appear only once in the bot's outfit.

Item equipping can be a fun way to customize your bot's appearance, adding to the overall gaming experience in Highrise. Always ensure the correct ID is used for the items when equipping them, to maintain the desired bot appearance. With this process, you can easily change the look of your bot as frequently as you'd like, providing an exciting opportunity for virtually endless customization.

### Active Palette

Some items can have different color palettes, indicated by setting the `active_palette` parameter in the Item object. The best example of this is "body-flesh," where this parameter can change skin tone. If you're unsure of an item's color palette, it's always safe to set it to `0`.

### Buying Items

Bots have a new endpoint that allows them to directly purchase an itemfrom the store with their gold using the `buy_item("item_id")` function or `BuyItemRequest` request on the bot API. Remember, bots can only purchase items readily available in the shop for gold—no collectible or grab items. An item’s ability to be bought is indicated in the data API via the `is_purchasable` parameter. Be mindful, bots can't trade items, so purchasing the same item more than once is pointless. Once purchased, the item will appear in the bot's inventory.

## Conclusion

While setting up your bot's outfit can be time-consuming, improvements are underway to simplify this process. For now, remember these key points:

* Bots can retrieve a list of items in their inventory using either `get_inventory()` or `GetInventoryRequest()`.
* Bots can check what they currently have equipped with `get_my_outfit()` or `GetUserOutfitRequest(bot_id)`.
* Users can check what other users have equipped using `get_user_outfit()` or `GetUserOutfitRequest(user_id)`.
* Bots can send a valid list of items (outfit) to change their appearance using `set_outfit(outfit)` or `SetOutfitRequest(outfit)`.
* Bots can equip any "free" item (items with rarity: none).
* While bots can buy items using `buy_item(item_id)` or `BuyItemRequest()`, ensure not to buy duplicates as bots can only use one of each item.