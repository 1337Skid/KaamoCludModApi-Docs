# Player

The `player` object gives you access to the player's data and actions

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `money` | `number` | The player's current money |
| `enemieskilled` | `number` | The number of enemies killed since the save was created |
| `level` | `number` | The player's level |
| `visitedstations` | `number` | The number of stations the player has visited |
| `cargosalvagedcount` | `number` | The number of cargo the player has salvaged |
| `asteroidsdestroyedcount` | `number` | The number of asteroids the player has destroyed |

Properties are readable and writable

```lua
print(player.money) -- get
player.money = 99999 -- set
```

## Methods

### GetShipInfo
Returns a table containing the player's ship information

```lua
local shipinfo = player:GetShipInfo()
print(shipinfo["cargo"])
print(shipinfo["maxcargo"])
print(shipinfo["armor"])
print(shipinfo["maxhealth"])
```

---

### SetShipInfo
Sets the player's ship information

!!! info "Args"
    `shipinfo` - A table containing the ship properties to update

```lua
local shipinfo = {
    maxcargo = 9999,
    armor = 9999,
    maxhealth = 9999
}
player:SetShipInfo(shipinfo)
```

---

### HasShipArmor
Returns `true` if the player's ship has an armor equipped

```lua
if player:HasShipArmor() then
    print("The ship has an armor")
end
```

---

### HasJumpDrive
Returns `true` if the player's ship has a jump drive equipped

```lua
if player:HasJumpDrive() then
    print("The ship has a jump drive")
end
```

---

### IsDocked
Returns `true` if the player is currently docked in a station

```lua
if player:IsDocked() then
    print("Player is docked")
end
```

---

### ToggleCloaking
Toggles the player's cloaking device

```lua
player:ToggleCloaking()
```

---

### SetPosition
Teleports the player to the given coordinates

!!! info "Args"
    `x`, `y`, `z` - The target coordinates

```lua
player:SetPosition(10, 10, 10)
```