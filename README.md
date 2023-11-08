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
> Checks if the player already has a glove config. Returns a `bool` value.

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
> Creates a new configuration instance with the attributes in AttributeTable. Also returns the `Configuration` it creates.

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
> You have to type the exact names of the attributes in AttributesTable. Currently, there are 10 attributes, and possibly more to come.
> These attributes are: `Ability`, `AbilityCooldown`, `AbilityState`, `CanAbility`, `CanSlap`, `EquipState`, `Kills`, `Power`, `SlapCooldown`, `SlapSpeed`.

---

## GloveHandler:ChangeConfig(Config, AttributeTable)
> Changes a new pre-existing configuration instance with the attributes in AttributeTable.

- **Config:** `Configuration`
- **AttributeTable:** `Table (Dictionary)`

```lua
local AttributesTable = {
    Ability = "Insanium",
    Power = 69,
    Kills = 69,
    SlapCooldown = 69,
}

local Config = GloveHandler:GetConfig(player)
if Config then
    GloveHandler:ChangeConfig(Config, AttributesTable)
end
```

> You do not have to specify every attribute in AttributesTable. The ones that aren't specified will be their previous values.
> You have to type the exact names of the attributes in AttributesTable. Currently, there are 10 attributes, and possibly more to come.
> These attributes are: `Ability`, `AbilityCooldown`, `AbilityState`, `CanAbility`, `CanSlap`, `EquipState`, `Kills`, `Power`, `SlapCooldown`, `SlapSpeed`.
> Don't use this if you only want to change one attribute, for that use Config:SetAttribute() instead.

---

## GloveHandler:SetCooldown(player, cooldownTime, cooldownType)
> Sets a cooldown for a player.

- **player:** `Player`
- **cooldownTime:** `Number`
- **cooldownType:** `String` **("Slap" or "Ability")**

---

## GloveHandler:IsOnCooldown(player, cooldownType)
> Checks if a player is on cooldown for the respective cooldown type. Returns a `bool` value.

- **player:** `Player`
- **cooldownType:** `String` **("Slap" or "Ability")**

---

## GloveHandler:GetRemainingCooldown(player, cooldownType)
> Returns the cooldown of a player for the respective cooldown type. Returns a `number` value.

- **player:** `Player`
- **cooldownType:** `String` **("Slap" or "Ability")**

---

## GloveHandler:Slap(player, Config, targetPart)
> Does a slappy slap. TargetPart should usually be the glove's hand.

- **player:** `Player`
- **Config:** `Configuration`
- **targetPart:** `Part`

> NOTE THAT YOU DO NOT HAVE TO MANUALLY SET COOLDOWNS, THE FUNCTION ALREADY DOES IT FOR YOU.
---

## GloveHandler:Ability(player, Config)
> Executes whatever ability is written in the Config.

- **player:** `Player`
- **Config:** `Configuration`

> NOTE THAT YOU DO NOT HAVE TO MANUALLY SET COOLDOWNS, THE FUNCTION ALREADY DOES IT FOR YOU.
