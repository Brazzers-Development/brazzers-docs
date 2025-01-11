# Snippets

## Cop Count

{% hint style="danger" %}
If you do not use Renewed Services and get your cop count differently, here are some snippets that can replace that callback
{% endhint %}

```lua
-- Make sure to include your frameworks shared object at the top of the file

local ESX = exports["es_extended"]:getSharedObject()
local QBCore = exports['qb-core']:GetCoreObject()


-- ESX Framework
lib.callback.register('brazzers-sales:server:copCount', function()
    local count = 0
    local players = ESX.GetExtendedPlayers("job", "police")
    
    for _, _ in pairs(players) do
        count += 1
    end
    
    return count
end)

-- QBCore Framework
lib.callback.register('brazzers-sales:server:copCount', function()
    local count = 0
    
    for _, v in pairs(QBCore.Functions.GetPlayers()) do
        local player = QBCore.Functions.GetPlayer(v)
        if player and (player.PlayerData.job.name == 'police') then
            count += 1
        end
    end
    
    return count
end)

-- QBX Framework
lib.callback.register('brazzers-sales:server:copCount', function()
    local count = 0
    
    for _, v in pairs(exports.qbx_core:GetQBPlayers()) do
        local player = exports.qbx_core:GetPlayer(v)
        if player and (player.PlayerData.job.name == 'police') then
            count += 1
        end
    end
    
    return count
end)
```

***

## Is Player Cop

{% hint style="danger" %}
If you do not use Renewed Services and check if a player is a cop differently, here are some snippets that can replace that callback
{% endhint %}

```lua
-- Make sure to include your frameworks shared object at the top of the file

local ESX = exports["es_extended"]:getSharedObject()
local QBCore = exports['qb-core']:GetCoreObject()

-- ESX Framework
lib.callback.register('brazzers-sales:server:isPlayerACop', function(source)
    local player = ESX.GetPlayerFromId(source)
    return player.job.name == 'police'
end)

-- QBCore Framework
lib.callback.register('brazzers-sales:server:isPlayerACop', function(source)
    local player = QBCore.Functions.GetPlayer(source)
    return player.PlayerData.job.name == 'police'
end)

-- QBX Framework
lib.callback.register('brazzers-sales:server:isPlayerACop', function(source)
    local player = exports.qbx_core:GetPlayer(source)
    return player.PlayerData.job.name == 'police'
end)
```

***
