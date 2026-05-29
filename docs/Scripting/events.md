# Events

events are fired when the action is triggered

## IsInGame
Fires when the player is in a save
!!! warning "Warning"

    This event isn't async, wait() does not work here
```lua
RegisterEvent("IsInGame", function()
	print("Joined")
end)
```
## OnJoinGame
Fires when the player loads a save
!!! warning "Warning"

    This event isn't async, wait() does not work here
```lua
RegisterEvent("OnJoinGame", function()
	print("Joined")
end)
```
## OnAsteroidDestroyed
Fires when the player destroy an asteroid
!!! info "Args"

    `count` returns the number of asteroids destroyed since the save was created
```lua
RegisterEvent("OnAsteroidDestroyed", function(count)
    wait(1)
	print("Asteroids destroyed : " .. count)
end)
```
## OnEnemieKilled
Fires when an enemie has been killed by the player
!!! info "Args"

    `count` returns the number of enemies killed since the save was created
```lua
RegisterEvent("OnEnemieKilled", function(count)
    wait(1)
	print("Enemies killed : " .. count)
end)
```
## OnCargoChanged
Fires when the player cargo changed
!!! info "Args"

    `count` returns the current cargo that the player hold
```lua
RegisterEvent("OnCargoChanged", function(count)
    wait(1)
	print("Current cargo : " .. count)
end)
```
## OnStationChanged
Fires when the player travels to a different station
!!! info "Args"

    `id` returns the current station id
```lua
RegisterEvent("OnStationChanged", function(id)
    wait(1)
	print("Station id is " .. id)
end)
```
## OnStationDocked
Fires when the player docked in a station
```lua
RegisterEvent("OnStationDocked", function()
    wait(1)
	print("You docked in this station " .. station.name)
end)
```
## IsInMainMenu
Fires when the player is in the main menu
!!! warning "Warning"

    This event isn't async, wait() does not work here
```lua
RegisterEvent("IsInMainMenu", function()
	print("Main menu")
end)
```
## OnMoneyChanged
Fires when the player money changed
!!! warning "Warning"

    This event isn't async, wait() does not work here
!!! info "Args"

    `money` returns the current player money
```lua
RegisterEvent("OnMoneyChanged", function(money)
	print("Current money : " .. money)
end)
```
## OnSystemChanged
Fires when the player travels to a different system
!!! info "Args"

    `id` returns the current system id
```lua
RegisterEvent("OnSystemChanged", function(id)
    wait(1)
	print("System id : " .. id)
end)
```
## OnUpdate
Fires every ticks
!!! warning "Warning"

    This event isn't async, wait() does not work here
```lua
RegisterEvent("OnUpdate", function()
	print("Update!")
end)
```
## EarlyInit
!!! warning "Warning"

    This event isn't async, wait() does not work here
!!! info "Args"

    This event is mandatory if you want to create new contents in the game such as custom ships, custom items and more
```lua
RegisterEvent("EarlyInit", function()
	print("Early init")
end)
```