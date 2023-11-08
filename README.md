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

---
# READ
This is for GloveConfig. There are TEN attributes at the moment, and possibly more to come. This will go over what they're used for.
To begin with, you HAVE to write the exact name of these attributes in AttributesList (for CreateConfig and ChangeConfig functions).

Ability `String`: This defines the ability of the glove. It is used to determine what the glove does when it's activated.
AbilityCooldown `Number`: The duration of the debounce whenever you activate the ability.
AbilityState `Bool`: The state of the ability. As long as the ability is ongoing, this should be true.
CanAbility `Bool`: Whether the player can use their ability at the moment.
CanSlap `Bool`: Whether the player can slap at the moment.
EquipState `Bool`: True while the glove is equipped, false while it's not. Currently doesn't have a use.
Kills `Number`: The number of kills you've gained in your current lifetime. Especially useful for Killstreak etc.
Power `Number`: How strong the knockback will be. The default is 50.
SlapCooldown `Number`: The duration of the debounce whenever you slap.
SlapSpeed `Number`: The speed of the glove's slap animation and how fast the hitbox gets deleted. The default is 50.

For Power and SlapSpeed, think of 50 as the default value. If you want to make it twice as strong, make it 100.
For SlapSpeed, 50 (aka the default value) means the animation will be over in 1 second, and the hitbox will be deleted in 1 second.
This means if you put it to 100, the animation will be over in 0.5 seconds and the hitbox will be deleted in 0.5 seconds.
