## Glove.new(Player, Glove, Power, Speed, Ability, AbilityCooldown)
> Creates new information for a glove. This should be used inside of a glove's server script.

- **Player:** `string` (Defaults to "None")
- **Glove:** `string` (Defaults to "Default")
- **Ability:** `string` (Defaults to "None")
- **Power:** `number` (Defaults to 50)
- **Speed:** `number` (Defaults to 50)
- **AbilityCooldown:** `number` (Defaults to 10)

```lua
local newGlove = Glove.new("SnowCliffx", "Default", "Blast", 25, 50, 10)
print(newGlove)
-- Would print out "{["Player"] = "SnowCliffx", ["Glove"] = "Default", ["Ability"] = "Blast", ["Power"] = 25, ["Speed"] = 50, ["AbilityCooldown"] = 10}"
```

> You have to use =="nil"== as an argument to set it to the default value.

```lua
local newGlove = Glove.new(nil, nil, "Teleport", nil, 40, 20)
print(newGlove)
-- Would print out "{["Player"] = "None", ["Glove"] = "Default", ["Ability"] = "Teleport", ["Power"] = 50, ["Speed"] = 40, ["AbilityCooldown"] = 20}"
```

---

## Glove:SetAbility(abilityName)
> Sets the glove's ability.

- **abilityName:** `string`
 
```lua
local newGlove = Glove.new("SnowCliffx", "Default", 25, 50, "Blast")
print(newGlove.Ability) -- Would print out "Blast"
newGlove:SetAbility("Teleport")
print(newGlove.Ability) -- Would print out "Teleport"
```
