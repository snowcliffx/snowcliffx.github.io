## Glove.new(Player, Glove, Power, Speed, Ability)
> Creates new information for a glove.

- **Player:** `string`
- **Glove:** `string`
- **Power:** `number`
- **Speed:** `number`
- **Ability:** `string`

```lua
local newGlove = Glove.new("SnowCliffx", "Default", 25, 50, "Blast")
print(newGlove)
-- Would print out:"{["Player"] = "SnowCliffx", ["Glove"] = "Default", ["Power"] = 25, ["Speed"] = 50, ["Ability"] = "Blast"}"
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
