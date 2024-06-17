# Types

The attribute `Type` is used to specify the type of script you are creating. The `Type` attribute can be set to `Client`, `Server`, `Module`, `ClientAndServer`, or `UI`.

<Note type="warning">
This is important for the Studio to know how to handle the script. And will be set automatically when creating a new script from the Studio.
</Note>

Here is an example of defining the script type in Lua:

[Client Type Script](https://create.highrise.game/learn/studio/create/scripting/script-types/client)
```lua
--!Type(Client)
```

[Server Type Script](https://create.highrise.game/learn/studio/create/scripting/script-types/server)
```lua
--!Type(Server)
```

[Module Type Script](https://create.highrise.game/learn/studio/create/scripting/script-types/module)
```lua
--!Type(Module)
```

[ClientAndServer Type Script](https://create.highrise.game/learn/studio/create/scripting/script-types/client-and-server)
```lua
--!Type(ClientAndServer)
```

[UI Type Script](https://create.highrise.game/learn/studio/create/scripting/script-types/ui)
```lua
--!Type(UI)
```

## Conclusion

By using the `Type` attribute, you can specify the type of script you are creating in Highrise Studio. This attribute helps the Studio identify the script's purpose and handle it accordingly, ensuring seamless integration and functionality within your game project.