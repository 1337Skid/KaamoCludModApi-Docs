# Contexts

Contexts expose variables and functions that are only available inside the hooked function

!!! info "Calling the real function"

    Every contexts has the `call` function

## MissionContext
### CreateFighter
This function creates a PlayerFighter class in the level
!!! info "Args"

    The first argument is the ship id<br>
    The second argument is the faction id
```lua
HookFunction("Level::createMission", function(ctx)
	print("Making a pirate ship")
    ctx:CreateFighter(0, 8) -- a pirate having a betty ship
end)
```
### CreateStaticObject
This function creates a PlayerStaticObject class in the level
!!! info "Args"

    The first argument is the object type<br>
    The second argument is the x position in the level<br>
    The third argument is the y position in the level<br>
    The fourth argument is the z position in the level
```lua
HookFunction("Level::createMission", function(ctx)
	print("Making a pirate station")
    ctx:CreateStaticObject(0, 55000, 5000, 10000) -- a pirate station at x=55000 y=5000 z=10000
end)
```

## GlobalsInitContext
### CreateShip
This function creates a new ship in the game
!!! info "Args"

    The first argument is the ship name<br>
    The second argument is the ship description<br>
    The third argument is the ship stats<br>
    The fourth argument is the diffuse texture id<br>
    The fifth argument is the normal texture id<br>
    The sixth argument is the material texture id<br>
    The last three arguments are the meshes lods id (lod0 to lod2) lods are meshes that can be different, it depends on your game graphics or if the model is far away of your camera
```lua
HookFunction("Globals::init", function(ctx)
	print("Creating a ship")
    -- primary_positions = the primary weapons
    -- secondary_positions = the secondary weapons
    local shipinfo = {
		armor = 160,
		maxcargo = 130,
		hangar_y = 160,
		primaryslots = 2,
		secondaryslots = 1,
		turretslots = 0,
		equipmentslots = 8,
		handling = 117,
		baseprice = 246568,
	    primary_positions = { {-33, 113, 120}, {35, 113, 120} },
	    secondary_positions = { {0, 133, 106} },
	    turret_positions = { {0, 0, 0} },
		engines = {
	    	{ pos = {0, 199, -336}, intensity = {0.4, 0.4, 0.4} }
		}
    }
    ctx:CreateShip("My ship", "A nice description", shipinfo, 1234, 1234, 1234, 1234, 1234)
end)
```
