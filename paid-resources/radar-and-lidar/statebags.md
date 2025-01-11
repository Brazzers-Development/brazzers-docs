---
icon: lock
---

# Statebags

### `jammer`

{% hint style="info" %}
Returns whether or not a vehicle has a radar jammer installed on it
{% endhint %}

* entity: `int`

```lua
local state = Entity(entity).state

if state?.jammer then
    -- Do stuff when jammer is installed
else
    -- Do stuff when jammer is not installed
end
```

***
