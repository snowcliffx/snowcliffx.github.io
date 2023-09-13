## Glove.new(Glove, Ability, Power, Speed, AbilityCooldown)
> Creates new information for a glove. This should be used inside of a glove's server script.

- **Glove:** `string` (Defaults to "Default")
- **Ability:** `string` (Defaults to "None")
- **Power:** `number` (Defaults to 50)
- **Speed:** `number` (Defaults to 50)
- **AbilityCooldown:** `number` (Defaults to 10)

- **AbilityState:** `boolean` (Default value, false)
- **EquipState:** `boolean` (Default value, false)

> If you required the ModuleScript as something else like "blabla" you have to use blabla.new().

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

## Glove:Equipped()
> Sets the glove's "EquipState" value to true.

```lua
local tool = script.Parent
local newGlove = Glove.new("leGlove", nil, 10, 10, 10)

tool.Equipped:Connect(function()
    newGlove:Equipped()
end)
```

## Glove:UnEquipped()
> Sets the glove's "EquipState" value to false.

```lua
tool.Unequipped:Connect(function()
    newGlove:UnEquipped()
end)
```

---

## Glove:SetInfo(Glove, Ability, Power, Speed, AbilityCooldown, AbilityState)
> Bulk re-creates glove info.

- **Glove:** `string`
- **Ability:** `string`
- **Power:** `number`
- **Speed:** `number`
- **AbilityCooldown:** `number`
- **AbilityState:** `boolean`

```lua
local newGlove = Glove.new("Default", "SpeedBoost", 50, 50, 10)
newGlove:SetInfo("Killstreak", "None", 40, 40, 0)
```

> You have to use **"nil"** as an argument to keep it as it is.

```lua
local newGlove = Glove.new("Default", "SpeedBoost", 30, 30, 5, false)
newGlove:SetInfo("God's Hand", nil, nil, 50, 30, true) -- Ability remains as "SpeedBoost" and power remains as 30.
```

> You also have access to individual set methods:

- **Glove:SetGlove(gloveName)**
- **Glove:SetAbility(abilityName)**
- **Glove:SetPower(powerValue)**
- **Glove:SetSpeed(speedValue)**
- **Glove:SetAbilityCooldown(cooldownValue)**
- **Glove:SetAbilityState(stateValue)**

---

## Glove:CreateHitbox(Handle, debrisTime)
> Creates a new hitbox at the handle's location and deletes it after debrisTime (seconds). The cooldown is calculated with 50/GloveSpeed.

- **Handle:** `Instance` (This should usually be the HAND part of the glove)
- **debrisTime:** `number` (Defaults to 1)

```lua
local tool = script.Parent
local handle = tool.Handle

Glove.new("Killstreak", nil, 20, 50, 0)

tool.Activated:Connect(function()
    glove:CreateHitbox(handle, 0.5)
end)
```

---
