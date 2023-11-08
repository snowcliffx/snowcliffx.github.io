## GloveHandler.Give(player, gloveName)
> Puts the glove as a tool in the Player's backpack. This should usually be used in a server script inside of a portal.

- **player:** `Player`
- **gloveName:** `String`

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

## GloveHandler:HasConfig(player)
> Checks if the player already has a glove config. Returns a bool value.

- **player:** `Player`

```lua
if GloveHandler:HasConfig(player) then
    print("player has config.")
else
    print("player doesn't have config.")
end
```

---

## GloveHandler:GetConfig(player)
> Returns the configuration instance of a player if they have one, otherwise returns false.

- **player:** `Player`

```lua
local Config = GloveHandler:GetConfig(player)
if Config then
    Config:Destroy()
end
```

---

## GloveHandler:CreateConfig(player, AttributeTable)
> Creates a new configuration instance with the attributes in AttributeTable. Also returns the instance it creates.

- **player:** `Player`
- **AttributeTable:** `Table (Dictionary)`

```lua
local AttributesTable = {
    Ability = "Fart",
    Power = 100,
    Kills = 5,
    SlapCooldown = 2,
}

local Config = GloveHandler:CreateConfig(player, AttributesTable)
```

> You do not have to specify every attribute in AttributesTable. The ones that aren't specified will be their default values.
> You have to type the exact names of the attributes in AttributesTable. Currently, there are 9 attributes, and possibly more to come.
> These attributes are: `Ability`, `AbilityCooldown`, `AbilityState`, `CanAbility`, `CanSlap`, `EquipState`, `Kills`, `Power`, `SlapCooldown`.
