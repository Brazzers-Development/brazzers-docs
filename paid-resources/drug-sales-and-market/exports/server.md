# Server

### `getRepAmount`

{% hint style="info" %}
Returns the amount of rep you have in the specific reputation
{% endhint %}

```lua
exports.brazzers_sales:getRepAmount(source, rep)
```

* source: `int`
  * 1
* rep: `string`
  * weed

***

### `addRep`

{% hint style="info" %}
Add reputation to a player
{% endhint %}

```lua
exports.brazzers_sales:addRep(source, rep, amount, chance)
```

* source: `int`
  * 1
* rep: `string`
  * weed
* amount: `int`&#x20;
  * 10
* chance: `int`&#x20;
  * 10

***

### `removeRep`

{% hint style="info" %}
Remove reputation to a player
{% endhint %}

```lua
exports.brazzers_sales:removeRep(source, rep, amount, chance)
```

* source: `int`
  * 1
* rep: `string`
  * weed
* amount: `int`&#x20;
  * 10
* chance: `int`&#x20;
  * 10

### `addRepByItem`

{% hint style="info" %}
Add reputation to a player that contains the item in the reputation. Ex. (weed reputation accepts joints)
{% endhint %}

```lua
exports.brazzers_sales:addRepByItem(source, item, amount, chance)
```

* source: `int`
  * 1
* item: `string`
  * joint
* amount: `int`&#x20;
  * 10
* chance: `int`&#x20;
  * 10

***

### `removeRepByItem`

{% hint style="info" %}
Remove reputation from a player that contains the item in the reputation. Ex. (weed reputation accepts joints)
{% endhint %}

```lua
exports.brazzers_sales:removeRepByItem(source, item, amount, chance)
```

* source: `int`
  * 1
* item: `string`
  * joint
* amount: `int`&#x20;
  * 10
* chance: `int`&#x20;
  * 10

***

### `hasSkill`

{% hint style="info" %}
Checks if a player has a specific skill
{% endhint %}

```lua
local skill = 'Big Booty Bandits'
local active = exports.brazzers_sales:hasSkill(source, skill)

if active then
    -- Do stuff when has skill
else
    -- Do stuff when you don't have the skill-
end
```

* source: `int`
  * 1
* skill: `string`
  * Big Booty Bandit

***

### `getHighestSkill`

{% hint style="info" %}
Gets the highest skill from a list of data
{% endhint %}

```lua
local data = {'Big Booty Bandit 1', 'Big Booty Bandit 2', 'Big Booty Bandit 3'}
local highest = exports.brazzers_sales:getHighestSkill(source, data)

-- If I have BBB1 and BBB3, it'll return BBB3 because its the highest I have.
-- Highest is determined by the order the data is in that I give the export.

if highest == 'Big Booty Bandit 3' then
    -- Do stuff cause im a BBB3
end
```

* source: `int`
  * 1
* data: `table`
  * {'Big Booty Bandit 1', 'Big Booty Bandit 2', 'Big Booty Bandit 3'}

***

### `unlockSkill`

{% hint style="info" %}
Unlock a skill for a player by skill name
{% endhint %}

```lua
local name = 'Big Booty Bandit 1'
local unlock = exports.brazzers_sales:unlockSkill(source, name)

if unlock then
    -- Do stuff when the skill unlocks
else
    -- Do stuff if it doesn't unlock
end
```

* source: `int`
  * 1
* name: `string`
  * Big Booty Bandit 1

***

### `lockSkill`

{% hint style="info" %}
Lock a skill for a player by skill name
{% endhint %}

```lua
local name = 'Big Booty Bandit 1'
local lock = exports.brazzers_sales:unlockSkill(lockSkill, name)

if lock then
    -- Do stuff when the skill locks
else
    -- Do stuff if it doesn't lock
end
```

* source: `int`
  * 1
* name: `string`
  * Big Booty Bandit 1

***

### `getMyMarketItems`

{% hint style="info" %}
Returns all my items in a table that are on the market
{% endhint %}

```lua
exports.brazzers_sales:getMyMarketItems(source)
```

* source: `int`
  * 1

***

### `getCart`

{% hint style="info" %}
Returns all my items in my cart
{% endhint %}

```lua
exports.brazzers_sales:getCart(source)
```

* source: `int`
  * 1

***

### `getAmountOfOffers`

{% hint style="info" %}
Returns the amount of offers I have on the market
{% endhint %}

```lua
exports.brazzers_sales:getAmountOfOffers(source)
```

* source: `int`
  * 1

***
