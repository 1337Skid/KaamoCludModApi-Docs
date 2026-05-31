# HookFunction

Hooks let you override the behavior of a function entirely

!!! info "Info"

    Every hooks are async which means wait() is available

## Level::createCampaignMission
This function is triggered when we join a station with a mission marker in, it can be a freelance mission or a campaign mission
!!! info "Args"

    `ctx` is the [MissionContext](contexts.md#missioncontext) context
```lua
HookFunction("Level::createCampaignMission", function(ctx)
	print("createCampaignMission has been called !")
	ctx:call() -- calling real function (you can remove the ctx:call() if you want to override the hooked function entirely)
end)
```

---


## Level::createMission
This function is triggered when we join a station without any missions, it can be really misleading due to of the function name being "createMission"
!!! info "Args"

    `ctx` is the [MissionContext](contexts.md#missioncontext) context
```lua
HookFunction("Level::createMission", function(ctx)
	print("I'm in a new station !")
	ctx:call() -- calling real function (you can remove the ctx:call() if you want to override the hooked function entirely)
end)
```

---


## Globals::init
This function is triggered when we start the game, this is really different from the EarlyInit function because EarlyInit is the modding api init and Globals::init is the game init
!!! info "Args"

    `ctx` is the [GlobalsInitContext](contexts.md#globalsinitcontext) context
!!! warning "Warning"

    Removing or calling `ctx:call()` will do nothing because if you were able to override Globals::init entirely the game would crash
```lua
HookFunction("Globals::init", function(ctx)
	print("Hello game")
end)
```