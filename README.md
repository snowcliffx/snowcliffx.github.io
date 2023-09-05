## Glove.new(Glove, Power, Speed, Ability, AbilityCooldown)
> Creates new information for a glove. This should be used inside of a glove's server script.

- **Glove:** `string` (Defaults to "Default")
- **Ability:** `string` (Defaults to "None")
- **Power:** `number` (Defaults to 50)
- **Speed:** `number` (Defaults to 50)
- **AbilityCooldown:** `number` (Defaults to 10)

```lua
local newGlove = Glove.new("Default", "Blast", 25, 50, 20)
print(newGlove)
-- Would print out "{["Glove"] = "Default", ["Ability"] = "Blast", ["Power"] = 25, ["Speed"] = 50, ["AbilityCooldown"] = 20}"
```

> You have to use **"nil"** as an argument to set it to the default value.

```lua
local newGlove = Glove.new(nil, "Teleport", nil, 40, nil)
print(newGlove)
-- Would print out "{["Glove"] = "Default", ["Ability"] = "Teleport", ["Power"] = 50, ["Speed"] = 40, ["AbilityCooldown"] = 10}"
```

---

## Glove.give(Player, Glove)
> Puts the glove as a tool in the Player's backpack. This should usually be used in a server script inside of a portal.

- **Player:** `Player`
- **Glove:** `string`

```lua
local Players = game:GetService("Players")

local portalPart = script.Parent

portalPart.Touched:Connect(function(hit)
    if hit.Parent:FindFirstChild("Humanoid") then
        local character = hit.Parent
        local player = Players:GetPlayerFromCharacter(character)
        Glove.give(player, "Default")
    end
end)
```

---

## Glove:CreateHitbox(Handle)
> Creates a new hitbox at the handle's location and deletes it after 0.5 seconds. The cooldown is calculated with (50 / GloveSpeed).

- **Handle:** `Instance` (This should usually be the HAND part of the glove.)

```lua
local tool = script.Parent
local handle = tool.Handle

glove.new("Killstreak", nil, 20, 50, 0)

tool.Activated:Connect(function()
    glove:CreateHitbox(handle)
end)
```

---

## Glove:SetAbility(Ability)
> Sets the glove's ability.

- **Ability:** `string`
 
```lua
local newGlove = Glove.new("aGlove", "Blast", 25, 50, 5)
print(newGlove.Ability) -- Would print out "Blast"
newGlove:SetAbility("Teleport")
print(newGlove.Ability) -- Would print out "Teleport"
```

---
dd
