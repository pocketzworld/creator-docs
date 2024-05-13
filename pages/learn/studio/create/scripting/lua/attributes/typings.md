# Types

The attribute `Type` is used to specify the type of script you are creating. This attribute is optional, but it is recommended to include it for clarity and consistency. The `Type` attribute can be set to `Client`, `Server`, `Module`, `ClientAndServer`, or `UI`.

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

Whether to include the `Type` attribute in your script depends on the context and purpose of the script. By specifying the script type, you can ensure that your script is correctly categorized and used in the intended context. This attribute helps maintain consistency and clarity in your project, making it easier to manage and organize your scripts effectively.