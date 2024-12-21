---
icon: lock
---

# Statebags

### zoom

***

Returns whether the player is currently zooming in or not

* zoom: `boolean`

```lua
local zoomed = LocalPlayer.state.zoom

if zoomed then
    -- Do stuff when zoomed
else
    -- Do stuff when not zoomed
end
```

### freeCam

***

Returns whether the player is currently using the freeCam or not

* freeCam: `boolean`

```lua
local usingFreeCam = LocalPlayer.state.freecam

if usingFreeCam then
    -- Do stuff when using free cam
else
    -- Do stuff when not using free cam
end
```
