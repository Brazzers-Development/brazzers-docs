# Server

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

<pre class="language-lua"><code class="lang-lua"><strong>local bolos = exports.brazzers_radar:getBolos()
</strong></code></pre>

***

### `toggleJammer`

{% hint style="info" %}
Install/ uninstall a vehicle jammer on a vehicle
{% endhint %}

```lua
exports.brazzers_radar:toggleJammer(bool, netId)
```

* bool: `boolean`
  * true
  * false
* netId: `int`
  * net id of the vehicle entity

***
