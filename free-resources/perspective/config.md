---
description: Here is a preview of the config for this resource
icon: code
---

# Config



```lua
return {
    enableZoom = true, -- Enable the ability to zoom your camera
    enableFreeCam = true, -- Enable or disable free cam
    ease = 200, -- Longer ease time just means the longer it takes to ease into the camera. Lower is quicker
    speed = 0.1, -- Movement speed for freecam
    distance = 5.0, -- Max distance the freecam can be from the player
    keys = { -- Default keys
        enableFreeCam = 'F3',
        freeCamForward = 'W',
        freeCamBackward = 'S',
        freeCamLeft = 'A',
        freeCamRight = 'D',
        freeCamUp = 'Q',
        freeCamDown = 'E',
        zoom = 'MOUSE_MIDDLE',
    },
}
```
