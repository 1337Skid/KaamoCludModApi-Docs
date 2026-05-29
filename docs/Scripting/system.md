# System

The `system` object gives you access to the current system's data and lets you create new systems

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `id` | `number` | The system's id |
| `name` | `string` | The system's name |
| `risk` | `number` | The system's risk level |
| `faction` | `number` | The system's faction |
| `jumpgatestationid` | `number` | The station id of the system's jump gate |
| `mapcoordinate_x` | `number` | The system's X coordinate on the map |
| `mapcoordinate_y` | `number` | The system's Y coordinate on the map |
| `mapcoordinate_z` | `number` | The system's Z coordinate on the map |

Properties are readable and writable

```lua
print(system.id) -- get
system.id = 12 -- set
```

## Methods

### Create
Creates a new system and returns its id

!!! warning "Warning"
    This method can only be called inside the `EarlyInit` event

!!! info "Args"
    - `name` - The system's name
    - `x`, `y`, `z` - The system's map coordinates
    - `faction` - The system's faction
    - `risk` - The system's risk level
    - `textureid` - The star texture id
    - `linkedsystemid` - The system id the jump gate links to. Pass `-1` for no jumpgate

```lua
RegisterEvent("EarlyInit", function()
    local systemid = system:Create("My system", 20, 30, 21, 2, 0, 7, 2)
    print("New system created, id: " .. systemid)
end)
```

---

### IsVisible
Returns `true` if the given system is visible on the map

!!! info "Args"
    `systemid` - The id of the system to check

```lua
if not system:IsVisible(26) then
    print("This system is not visible")
end
```

---

### SetVisible
Sets the visibility of a system on the map

!!! info "Args"
    - `systemid` - The id of the system to update
    - `visible` - `true` to show the system, `false` to hide it

```lua
system:SetVisible(26, true)
```