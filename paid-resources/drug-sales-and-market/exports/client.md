# Client

### `inDelivery`

{% hint style="info" %}
Checks if a player is in a delivery or not
{% endhint %}

<pre class="language-lua"><code class="lang-lua"><strong>local activeDelivery = exports.brazzers_sales:inDelivery()
</strong><strong>
</strong><strong>if activeDelivery then
</strong><strong>    -- do stuff when delivery is active
</strong><strong>else
</strong><strong>    -- do stuff when delivery is inactive
</strong><strong>end
</strong></code></pre>

***

### `getRepAmount`

{% hint style="info" %}
Returns the amount of rep you have in the specific reputation
{% endhint %}

```lua
exports.brazzers_sales:getRepAmount(rep)
```

* rep: `string`
  * weed

***

### `getAllRep`

{% hint style="info" %}
Gets all your rep in a table
{% endhint %}

```lua
exports.brazzers_sales:getAllRep()
```

***

### `hasSkill`

{% hint style="info" %}
Checks if a player has a specific skill
{% endhint %}

```lua
local skill = 'Big Booty Bandits'
local active = exports.brazzers_sales:hasSkill(skill)

if active then
    -- Do stuff when has skill
else
    -- Do stuff when you don't have the skill-
end
```

* skill: `string`
  * Big Booty Bandit

***

### `getHighestSkill`

{% hint style="info" %}
Gets the highest skill from a list of data
{% endhint %}

```lua
local data = {'Big Booty Bandit 1', 'Big Booty Bandit 2', 'Big Booty Bandit 3'}
local highest = exports.brazzers_sales:getHighestSkill(data)

-- If I have BBB1 and BBB3, it'll return BBB3 because its the highest I have.
-- Highest is determined by the order the data is in that I give the export.

if highest == 'Big Booty Bandit 3' then
    -- Do stuff cause im a BBB3
end
```

* data: `table`
  * {'Big Booty Bandit 1', 'Big Booty Bandit 2', 'Big Booty Bandit 3'}

***

### `getMyMarketItems`

{% hint style="info" %}
Returns all my items in a table that are on the market
{% endhint %}

```lua
exports.brazzers_sales:getMyMarketItems()
```

***

### `getCart`

{% hint style="info" %}
Returns all my items in my cart
{% endhint %}

```lua
exports.brazzers_sales:getCart()
```

***

### `getAmountOfOffers`

{% hint style="info" %}
Returns the amount of offers I have on the market
{% endhint %}

```lua
exports.brazzers_sales:getAmountOfOffers()
```

***

### `openMenu`

{% hint style="info" %}
Opens the drug menu
{% endhint %}

```lua
exports.brazzers_sales:openMenu()
```

***

### `closeMenu`

{% hint style="info" %}
Closes the drug menu
{% endhint %}

```lua
exports.brazzers_sales:closeMenu()
```

***
