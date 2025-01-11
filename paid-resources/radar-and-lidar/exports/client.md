# Client

### `addBolo`

{% hint style="info" %}
Flag the plate of a vehicle
{% endhint %}

```lua
exports.brazzers_radar:addBolo(plate)
```

* plate: `string`
  * BRAZZERS

***

### `removeBolo`

{% hint style="info" %}
Remove the flagged status from a plate
{% endhint %}

```lua
exports.brazzers_radar:removeBolo(plate)
```

* plate: `string`
  * BRAZZERS

***

### `getBolos`

{% hint style="info" %}
Gets all the plates that currently have a BOLO or are flagged
{% endhint %}

```lua
local bolos = exports.brazzers_radar:getBolos()
```

***

### `toggleJammer`

{% hint style="info" %}
Install/ uninstall a vehicle jammer on a vehicle
{% endhint %}

```lua
exports.brazzers_radar:toggleJammer(bool, vehicle)
```

* bool: `boolean`
  * true
  * false
* vehicle: `int`
  * entity

***
