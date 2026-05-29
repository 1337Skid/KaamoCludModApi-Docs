# Mission

The `mission` object gives you access to the current mission's data and lets you create and manage missions

## Properties

| Property | Type | Description |
|----------|------|-------------|
| `id` | `number` | The current campaign mission id |
| `completedsidemissions` | `number` | The number of completed side missions |

Properties are readable and writable

```lua
print(mission.id) -- get
mission.id = 10 -- set
```

## Methods

### Create
Creates a new custom mission and returns its id

!!! warning "Warning"
    This method can only be called inside the `EarlyInit` event

!!! info "Args"
    - `stationid` - The station id where the mission marker will appear
    - `description` - The mission description shown to the player
    - `type` - The mission type: `0` for campaign, `1` for freelance

```lua
RegisterEvent("EarlyInit", function()
    local missionid = mission:Create(10, "my mission !", 0)
end)
```

---

### Enable
Makes the mission marker visible and activates the custom mission

!!! info "Args"
    `missionid` - The id of the custom mission to enable

```lua
mission:Enable(missionid)
```

---

### Disable
Hides the mission marker and deactivates the custom mission

!!! info "Args"
    `missionid` - The id of the custom mission to disable

```lua
mission:Disable(missionid)
```

---

### EnableValkyrie
Enables the Valkyrie campaign

```lua
mission:EnableValkyrie()
```

---

### NextCampaignMission
Advances the campaign to the next mission

```lua
mission:NextCampaignMission()
```