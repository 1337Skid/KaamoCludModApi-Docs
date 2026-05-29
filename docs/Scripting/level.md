# Level

The `level` object lets you interact with the current level, such as spawning entities, creating cutscenes and sending radio messages

## Methods

### CreateRadioMessage
Displays a radio message on the screen

!!! info "Args"
    - `name` - The sender's name
    - `content` - The message content
    - `imageinfo` - A table describing the sender's portrait

```lua
local imageinfo = {
    race = 6,
    hair = 0,
    eyes = 0,
    mouth = 0,
    armor = 0
}
level:CreateRadioMessage("Keith T. Maxwell", "Hello!", imageinfo)
```

---

### CreateDialogueWindow
Opens a dialogue window with a sequence of messages

!!! info "Args"
    `dialogues` - A table of dialogue entries. Each entry has the following fields:

| Field | Type | Description |
|-------|------|-------------|
| `name` | `string` | The speaker's name |
| `content` | `string` | The spoken line |
| `image` | `table` | The speaker's portrait as `{race, hair, eyes, mouth, armor}` |
| `isplayer` | `number` | `1` if this is the player speaking, `0` otherwise |

```lua
local dialogues = {
    { name = "Keith T. Maxwell", content = "Hello!", image = {0, 0, 0, 0, 0}, isplayer = 1 },
    { name = "lil snail",        content = "Hi!",    image = {6, 1, 2, 0, 0}, isplayer = 0 },
}
level:CreateDialogueWindow(dialogues)
```

---

### CreateCutScene
Plays a cutscene by moving the camera through a sequence of points

!!! info "Args"
    `points` - A table of camera points. Each point has the following fields:

| Field | Type | Description |
|-------|------|-------------|
| `pos` | `table` | The camera position as `{x, y, z}` |
| `duration` | `number` | How long the camera stays at this point (in seconds) |
| `shake` | `number` | (optional) Camera shake intensity |
| `shakefrequency` | `number` | (optional) Camera shake frequency |

```lua
local points = {
    { pos = {0, 8000, 0},     duration = 5 },
    { pos = {2500, 200, 0},   duration = 5, shake = 8.0, shakefrequency = 100 },
    { pos = {0, 0, 30000},    duration = 5 },
}
level:CreateCutScene(points)
```

---

### CreateRoute
Creates a route from a list of positions and returns a [Route](placeholder.md#route) object

!!! info "Args"
    `pospoints` - A table of positions, each as `{x, y, z}`

```lua
local route = level:CreateRoute({
    { 100000.0, 0.0, 100000.0 },
    { 200000.0, 0.0, 200000.0 },
    { 300000.0, 0.0, 100000.0 },
})
if route:IsValid() then
    level:GetEntities()[2]:SetRoute(route)
end
```

---

### GetEntities
Returns a table of all active entities in the current level

```lua
local entities = level:GetEntities()
for k, v in pairs(entities) do
    print(v)
end
```

---

### CreateAsteroid
Spawns an asteroid in the level

!!! info "Args"
    - `x`, `y`, `z` - The spawn position
    - `scale` - The asteroid's scale
    - `meshid` - The mesh id to use for the asteroid

```lua
level:CreateAsteroid(0, 0, 50000, 30, 17000)
```