# GloveHandler Documentation

## Glove.new(player, glove, power, speed, ability)
> Creates new information for a glove.

- **player:** `string`
- **glove:** `string`
- **power:** `number`
- **speed:** `number`
- **ability:** `string`

```lua
local newGlove = Glove.new("SnowCliffx", "Default", 25, 50, "Blast")
print(newGlove)
-- Would print out:"{["Player"] = "SnowCliffx", ["Glove"] = "Default", ["Power"] = 25, ["Speed"] = 50, ["Ability"] = "Blast"}"
```

---

## Glove:SetAbility(ability)
> Sets the glove's ability.

- **ability:** `string`
 
```lua
local newGlove = Glove.new("SnowCliffx", "Default", 25, 50, "Blast")
print(newGlove.Ability) -- Would print out "Blast"
newGlove:SetAbility("Teleport")
print(newGlove.Ability) -- Would print out "Teleport"
```
