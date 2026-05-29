# Item

The `item` object lets you create custom items

## Methods

### Create
Creates a new item and returns its id

!!! warning "Warning"
    This method can only be called inside the `EarlyInit` event

!!! info "Args"
    - `name` - The item's name
    - `description` - The item's description
    - `iteminfo` - A table containing the item's properties (see below)

#### iteminfo table

| Field | Type | Description |
|-------|------|-------------|
| `type` | `string` | The item type (e.g. `"Laser"`) |
| `techlevel` | `number` | The item's tech level |
| `baseprice` | `number` | The item's base price |
| `minprice` | `number` | The item's minimum price |
| `maxprice` | `number` | The item's maximum price |
| `damage` | `number` | The item's damage (weapons only) |
| `loadingspeed` | `number` | The item's loading speed (weapons only) |
| `range` | `number` | The item's range (weapons only) |
| `speed` | `number` | The item's projectile speed (weapons only) |

```lua
RegisterEvent("EarlyInit", function()
    local iteminfo = {
        type = "Laser",
        techlevel = 9,
        baseprice = 1234,
        minprice = 12,
        maxprice = 1234,
        damage = 120,
        loadingspeed = 1300,
        range = 1000,
        speed = 3000
    }
    local itemid = item:Create("My Laser", "A very powerful laser", iteminfo)
    print("Item created with id: " .. itemid)
end)
```

!!! tip "Tip"
    Store the returned id in a variable so you can reference the item later (e.g. to add it to a station's hangar or remove it)