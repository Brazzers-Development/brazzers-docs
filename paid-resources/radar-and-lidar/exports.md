---
icon: arrow-down-left-and-arrow-up-right-to-center
---

# Exports



## Client

***

### _addBolo_

***

Flag the plate of a vehicle

```lua
exports.brazzers_radar:addBolo(plate)
```

* plate: `string`
  * BRAZZERS

### _removeBolo_

***

Remove the flagged status from a plate

```lua
exports.brazzers_radar:removeBolo(plate)
```

* plate: `string`
  * BRAZZERS

### _getBolos_

***

Gets all the plates that currently have a BOLO or are flagged

```lua
local bolos = exports.brazzers_radar:getBolos()
```

### _toggleJammer_

***

Install/ uninstall a vehicle jammer on a vehicle

```lua
exports.brazzers_radar:toggleJammer(bool, vehicle)
```

* bool: `boolean`
  * true
  * false
* vehicle: `int`
  * entity

## Server

***

### _addBolo_

Flag the plate of a vehicle

```lua
exports.brazzers_radar:addBolo(plate)
```

* plate: `string`
  * BRAZZERS

### _removeBolo_

***

Remove the flagged status from a plate

```lua
exports.brazzers_radar:removeBolo(plate)
```

* plate: `string`
  * BRAZZERS

### _getBolos_

***

Gets all the plates that currently have a BOLO or are flagged

<pre class="language-lua"><code class="lang-lua"><strong>local bolos = exports.brazzers_radar:getBolos()
</strong></code></pre>

### _toggleJammer_

***

Install/ uninstall a vehicle jammer on a vehicle

```lua
exports.brazzers_radar:toggleJammer(bool, netId)
```

* bool: `boolean`
  * true
  * false
* netId: `int`
  * net id of the vehicle entity
