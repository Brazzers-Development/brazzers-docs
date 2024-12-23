---
icon: code
description: Here is a preview of the config for this resource
---

# Config

```lua
return {
    defaultKeys = {
        toggleRadarMenu = 'F5',
        detectLidar = 'MOUSE_LEFT',
        toggleVehRadar = 'F7',
        toggleRadarLock = 'F6',
        directionalUp = 'UP',
        directionalDown = 'DOWN',
        directionalLeft = 'LEFT',
        directionalRight = 'RIGHT',
    },

    -- [SPEED] --
    speed = {
        mode = 'MPH', -- 'KMH' or 'MPH'
    },

    -- [RADAR] --
    radar = {
        retrictByJob = true, -- Would you like to restrict the radar usage by job names
        jobs = { 'police' }, -- If above is true, what job names
        class = { [18] = true }, -- Class of vehicles you want to allow (Default: Emergency)
        whitelist = { [`police`] }, -- Individual vehicles that you want to whitelist which will bypass class check
        distance = 25.0, -- Minimum distance the vehicle radar can read a vehicle
    },

    -- [LIDAR] --
    lidar = {
        command = {
            enabled = false, -- This command is used to replace the item dependency and ox_inventory. If you plan to use the item leave this false
            name = 'lidar' -- If enabled then do /lidar
        },
        item = 'WEAPON_PROLASER4', -- If above is false, this is the item name for the lidar weapon. I don't recommend changing this
        retrictByJob = true, -- Would you like to restrict the radar usage by job names
        jobs = { 'police' }, -- If above is true, what job names
        whitelist = { ['1001'] } -- Individual characters that you want to whitelist which will bypass job check
    },

    -- [SETTINGS MENU] --
    menu = {
        retrictByJob = true, -- Would you like to restrict the settings menu by job names
        jobs = { 'police' }, -- If above is true, what job names
    },

    -- [BOLOS] --
    bolos = {
        enableCommands = true, -- Commands for flagging and removing flagged plates
        retrictByJob = true, -- Would you like to restrict the command usage by job names [Recommended]
        jobs = { 'police' }, -- If above is true, what job names
    },

    -- [RADAR JAMMER]--
    jammer = {
        restrictByVehicle = false, -- Restrict the jammer item to being installed in certain vehicles
        whitelist = { [`sultan`] }, -- If above it true, add the vehicles that you want to whitelist
        backlist = { [`police`] }, -- General blacklist restricting these vehicles to install jammers on
    },

    -- [DIRECTIONAL MODE] --
    directional = {
        size = 1.0, -- Size of the sphere radius
        movement = 0.07, -- Speed of the sphere during edit mode
        distance = 10.0, -- Max distance sphere can move from the vehicle
    },

    -- [MISC CONFIG] --
    misc = {
        wait = 150, -- Wait period (ms) for updating radar values ([lower] = less optimized, faster updates, [higher] = more optimized, slower updates)
        reticle = true, -- Do you want to use the default crosshair for the lidar gun
    },

    -- [DEFAULT SETTINGS] --
    default = {
        theme = 'Green', -- Green, Blue, Yellow, White, Teal, Orange, Pink
        lidarScale = 1.8, -- Default scale of the lidar
        radarScale = 1, -- Default scale of the vehicle radar
        defaultFastLimit = 65, -- Default speed for the fast limit option
    },

    -- [CLASSES] -- 
    class = {
        [0] = 'COM', -- Compact
        [1] = 'SED', -- Sedan
        [2] = 'SUV', -- SUV
        [3] = 'COU', -- Coupe
        [4] = 'MUS', -- Muscle
        [5] = 'SPC', -- Sports Classics
        [6] = 'SPR', -- Sports
        [7] = 'SUP', -- Super
        [8] = 'MTC', -- Motorcycles
        [9] = 'OFF', -- Off-road
        [10] = 'IND', -- Industrial
        [11] = 'UTL', -- Utility
        [12] = 'VAN', -- Van
        [13] = 'CYC', -- Cycle
        [14] = 'BOA', -- Boat
        [15] = 'HEL', -- Helicopter
        [16] = 'PLN', -- Plane
        [17] = 'SRV', -- Service
        [18] = 'EMG', -- Emergency
        [19] = 'MIL', -- Military
        [20] = 'COM', -- Commercial
        [21] = 'TRN', -- Train
        [22] = 'OPW', -- Open Wheel
    },
}
```
