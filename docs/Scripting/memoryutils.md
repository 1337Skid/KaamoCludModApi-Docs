# MemoryUtils

The `memoryutils` object lets you patch the game's memory directly. This is useful for enabling or disabling game behaviors at a low level

!!! danger "Danger"
    Patching the wrong address or value can crash the game. Only use this if you know what you're doing

## Methods

### PatchByte
Writes a single byte to the given memory address

!!! info "Args"
    - `address` - The memory address to patch (as a hexadecimal number)
    - `value` - The byte value to write (`0x00` to `0xFF`)

```lua
RegisterEvent("EarlyInit", function()
    memoryutils:PatchByte(0x4AF717, 0x90)
    memoryutils:PatchByte(0x4AF718, 0x90)
end)
```

!!! tip "Tip"
    `0x90` is the x86 `NOP` instruction