# Asset

The `asset` object lets you load, edit and create game assets such as textures, meshes and materials

## Methods

### GetAssetFilePath
Returns the file path of an asset by its id

!!! info "Args"
    `id` - The asset's id

```lua
print(asset:GetAssetFilePath(2050)) -- 2050 is the interface asset
```

---

### SetAssetFilePath
Replaces an asset's file with a custom one

!!! warning "Warning"
    The replacement won't be visible immediately. The asset is reloaded when the game refreshes it (e.g. traveling to a station or changing system)

!!! info "Args"
    - `id` - The asset's id to replace
    - `filepath` - The path to your custom asset file

```lua
RegisterEvent("IsInMainMenu", function()
    asset:SetAssetFilePath(2050, "mods/my_mod/my_assets/custom_interface.aei")
end)
```

---

### GetText
Returns a localized text string by its id

!!! info "Args"
    `id` - The text string's id

```lua
print(asset:GetText(1059))
```

---

### CreateTexture
Loads a texture from a file and returns its id

!!! info "Args"
    `filepath` - The path to the texture file (`.aei`)

```lua
HookFunction("Globals::init", function(ctx)
    local diffuse = asset:CreateTexture("mods/my_mod/diffuse.aei")
end)
```

---

### CreateMaterial
Creates a material from textures and returns its id

!!! info "Args"
    - `diffuse` - The diffuse texture id
    - `normal` - The normal texture id
    - `shader` - The shader id

```lua
HookFunction("Globals::init", function(ctx)
    local diffuse = asset:CreateTexture("mods/my_mod/diffuse.aei")
    local normal = asset:CreateTexture("mods/my_mod/normal.aei")
    local material = asset:CreateMaterial(diffuse, normal, 29)
end)
```

---

### CreateMesh
Loads a mesh from a file and returns its id

!!! info "Args"
    - `filepath` - The path to the mesh file (`.aem`)
    - `materialid` - The material id to apply to the mesh

```lua
HookFunction("Globals::init", function(ctx)
    local material = asset:CreateMaterial(diffuse, normal, 29)
    local lod = asset:CreateMesh("mods/my_mod/model.aem", material)
end)
```