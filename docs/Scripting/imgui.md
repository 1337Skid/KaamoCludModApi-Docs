# ImGui

The `imgui` object lets you build in game mod menus using Dear ImGui widgets. Windows are registered with `RegisterWindow` and rendered every frame

## RegisterWindow
Registers a new ImGui window with a toggle key

!!! info "Args"
    - `title` - The window title shown in the title bar
    - `draw` - The draw callback, called every frame while the window is open
    - `togglekey` - The [virtual key code](https://learn.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes) used to toggle the window
    - `lockinput` - `1` to lock mouse and keyboard input while the window is open, `0` to allow movement

```lua
local KEY_INSERT = 0x2D

RegisterWindow("My mod menu", function()
    imgui:Text("Hello!!")
end, KEY_INSERT, 1)
```

---

## Widgets

### Text
Displays a line of text

!!! info "Args"
    `text` - The text to display

```lua
imgui:Text("Hello World")
```

---

### ColoredText
Displays a line of text with a custom color

!!! info "Args"
    - `text` - The text to display
    - `r`, `g`, `b`, `a` - The color components, each between `0.0` and `1.0`

```lua
imgui:ColoredText("Press insert to toggle", 0.4, 1.0, 0.4, 1.0)
```

---

### Button
Displays a button and returns `true` if it was clicked

!!! info "Args"
    `text` - The button label

```lua
if imgui:Button("Give 99999 Credits") then
    player.money = 99999
end
```

---

### Checkbox
Displays a checkbox and returns the current boolean state

!!! info "Args"
    - `text` - The checkbox label
    - `value` - The current boolean state

```lua
god_mode = imgui:Checkbox("God Mode", god_mode)
```

---

### SliderFloat
Displays a float slider and returns the current value

!!! info "Args"
    - `text` - The slider label
    - `value` - The current float value
    - `min` - The minimum value
    - `max` - The maximum value

```lua
local speed = 0.0
speed = imgui:SliderFloat("Speed", speed, 0.0, 100.0)
```

---

### SliderInt
Displays an integer slider and returns the current value

!!! info "Args"
    - `text` - The slider label
    - `value` - The current integer value
    - `min` - The minimum value
    - `max` - The maximum value

```lua
local credits = 0
credits = imgui:SliderInt("Money", credits, 0, 999999)
if imgui:Button("Apply Money") then
    player.money = credits
end
```

---

### InputText
Displays a text input field and returns the current string value

!!! info "Args"
    - `text` - The input label
    - `value` - The current string value

```lua
local name = ""
name = imgui:InputText("Name", name)
```

---

### InputFloat
Displays a float input field and returns the current value

!!! info "Args"
    - `text` - The input label
    - `value` - The current float value

```lua
local x = 0.0
x = imgui:InputFloat("Position X", x)
```

---

### InputInt
Displays an integer input field and returns the current value

!!! info "Args"
    - `text` - The input label
    - `value` - The current integer value

```lua
local count = 0
count = imgui:InputInt("Count", count)
```

---

## Layout

### Separator
Draws a horizontal separator line

```lua
imgui:Separator()
```

---

### SameLine
Places the next widget on the same line as the previous one

```lua
imgui:Button("A")
imgui:SameLine()
imgui:Button("B")
```

---

### Spacing
Adds a blank line of vertical spacing

```lua
imgui:Spacing()
```

---

## Frame

### SetWindowOpen
Displays the ImGui window

!!! info "Args"
    - `title` - The window title
    - `isopen` - Visible state of the window

```lua
imgui:SetWindowOpen("My mod menu", false) -- hide the window
```

---

### IsWindowOpen
Returns true if the ImGui window is open

!!! info "Args"
    - `title` - The window title

```lua
if imgui:IsWindowOpen("My mod menu") then
    print("Yes the window is open!")
end
```