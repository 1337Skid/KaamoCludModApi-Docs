# Station

The `station` object gives you access to the current station's data and lets you create and manage stations

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `id` | `number` | The station's id |
| `name` | `string` | The station's name |
| `level` | `number` | The station's tech level |
| `hangaritemscount` | `number` | The number of items in the station's hangar |
| `hangarshipscount` | `number` | The number of ships in the station's hangar |
| `agentscount` | `number` | The number of agents in the station |

Properties are readable and writable

```lua
print(station.level) -- get
station.level = 10
```

## Methods

### Create
Creates a new station and returns its id

!!! warning "Warning"
    This method can only be called inside the `EarlyInit` event

!!! info "Args"
    - `name` - The station's name
    - `techlevel` - The station's tech level
    - `textureid` - The planet texture id
    - `systemid` - The id of the system to place the station in

```lua
RegisterEvent("EarlyInit", function()
    local stationid = station:Create("my station", 8, 1, 26)
end)
```

---

### IsVoid
Returns `true` if the current station is a void station

```lua
if station:IsVoid() then
    print("You are in the void station")
end
```

---

### AddHangarShip
Adds a ship to the station's hangar

!!! info "Args"
    `shipid` - The id of the ship to add

```lua
station:AddHangarShip(0) -- add betty
```

---

### SetHangarShipInfo
Updates the info of a ship in the station's hangar

!!! info "Args"
    - `slotid` - The hangar slot index
    - `shipinfo` - A table containing the ship properties to update

```lua
local shipinfo = {
    id = 10,
    price = 50000
}
station:SetHangarShipInfo(0, shipinfo)
```

---

### HasItemInHangar
Returns `true` if the station's hangar contains the given item

!!! info "Args"
    `itemid` - The id of the item to check

```lua
if station:HasItemInHangar(1) then
    print("Item is in the hangar")
end
```

---

### RemoveHangarItem
Removes an item from the station's hangar

!!! info "Args"
    `itemid` - The id of the item to remove

```lua
station:RemoveHangarItem(196)
```

---

### GetAgentName
Returns the name of an agent at the given index

!!! info "Args"
    `index` - The agent's index (starting from `0`)

```lua
for i = 0, station.agentscount - 1 do
    print(station:GetAgentName(i))
end
```

---

### GetAgentFaction
Returns the faction of an agent at the given index

!!! info "Args"
    `index` - The agent's index (starting from `0`)

```lua
print(station:GetAgentFaction(0))
```

---

### CreateAgent
Creates a new agent in the current station

!!! warning "Warning"
    The game deletes the agent when you visit at least 3 stations, do your own checks if the agent has been already made (if the player join the same system then you can have duplicated agents)

!!! info "Args"
    - `name` - The agent's name
    - `factiontype` - The agent's faction
    - `isterranwoman` - Pass `1` for a female terran model, `-1` otherwise
    - `imageinfo` - A table describing the agent's portrait
    - `agentinfo` - A table describing the agent's behavior and dialogue

```lua
RegisterEvent("OnSystemChanged", function(id)
    local imageinfo = {
	    race = 0,
	    hair = 0,
	    eyes = 0,
	    mouth = 0,
	    armor = 0
    }
    agentsinfo.basic_talking = {
	    talking_type = 1,
	    talking_string = 1059
    }
    station:CreateAgent("Hello agent", 0, -1, imageinfo, agentinfo)
end)
```