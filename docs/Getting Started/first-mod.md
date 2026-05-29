# Your first mod

This guide is helpful as a quick start to create a mod.

---

## Folder structure

Create a folder inside `mods/` with your mod's name. The modding api will automatically load the file `init.lua` from it:

```
mods/
└── mymod/
    └── init.lua
```

!!! info "Mods loading order"

    The modding api loads the mods by alphabetical order
    if you want your mod to be the first loaded mod you can name the folder `00_mymod`
    mods loading order is really important if you are making new contents in the game

---

## Hello World

Open `init.lua` and add:

```lua
print("My mod is loaded")
```

Launch the game, you should see "My mod is loaded" in the modding api console

---

## Game events

Here's a slightly more interesting mod that prints info whenever you jump to a new system:

```lua
RegisterEvent("OnSystemChanged", function(id)
    print("You jumped to system #" .. id .. " (" .. system.name .. ")")
    print("Risk level: " .. system.risk)
    print("Your credits: " .. player.money)
end)
```

Let's add another event, if we go to a station we increase the player money to 1000

```lua
RegisterEvent("OnStationChanged", function(id)
    player.money = player.money + 1000
end)
```

There are a tons of events in the modding api feel free to [check this out](../Scripting/events.md)

## Final code
```lua
print("My mod is loaded")

RegisterEvent("OnSystemChanged", function(id)
    print("You jumped to system #" .. id .. " (" .. system.name .. ")")
    print("Risk level: " .. system.risk)
    print("Your credits: " .. player.money)
end)

RegisterEvent("OnStationChanged", function(id)
    player.money = player.money + 1000
end)
```

You can see more mods example [here](https://github.com/1337Skid/KaamoClubModApi/tree/main/mods_examples). 