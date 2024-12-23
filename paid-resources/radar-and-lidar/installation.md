---
icon: gear
description: Quick and easy tutorial to ensure the resource is installed properly
---

# Installation

## Installing The Item

***

* Head over to ox\_inventory/data/weapons.lua and paste the following item

```lua
['WEAPON_PROLASER4'] = {
	label = 'Lidar',
	weight = 700,
	durability = 0.1,
},
```

* Head over to ox\_inventory/data/items.lua and past the following item

```lua
['jammer'] = {
	label = 'Radar Jammer',
	weight = 500,
	stack = false,
	client = {
		export = 'brazzers_radar.jammer',
		image = 'jammer.png',
	}
},
```

* Locate the image for the item in brazzers\_radar/images and drag and drop that into ox\_inventory/web/images
