# Configuration

## Creating A Skill

{% hint style="info" %}
Locate data/skills.lua
{% endhint %}

```lua
{
    label = 'Meth', -- Label of the specialization
    identifier = 'meth', -- Make this unique
    skills = {
        {
            label = 'Meth Head', -- Label of the skill (should be unique and different for each skill)
            description = 'I can\'t stop being meth upped', -- Description of the skill
            icon = 'fa-solid fa-seedling', -- Icon for the skill in the menu
            requirements = { -- Requirements to unlock the skill
                { label = '25 Meth Reputation', reputation = 'meth', value = 25 },
            },
            rewards = { -- These are all the available types of rewards
                { type = 'money', money = 'cash', amount = 500 },
                { type = 'item', item = 'lockpick', amount = 1, metadata = {} },
                { type = 'reputation', rep = 'meth', amount = 10 },
            },
            row = 1, -- This number reflects the row in the skill tree
        },
        -- continue making more skills if you'd like
    }
}
```

***

## Creating Reputation

{% hint style="info" %}
After creating your skills, now you need to add the reputation linking your rep to the new skill tree. Locate data/reputation.lua
{% endhint %}

```lua
{
    label = 'Meth', -- Label for the reputation
    icon = 'fa-solid fa-seedling', -- Icon associated with this reputation.
    identifier = 'meth', -- This identifier must match the one you created in skills to link them
    items = { -- List of items that can increase the reputation when sold
        'meth',
    },
    cornering = { -- Allow rep earnings in cornering
        enabled = true, -- Enable or disable rep earnings in cornering
        chance = 10, -- Chance in percentage, that'll give rep to the player each handoff
        amount = { min = 1, max = 5 }, -- Amount of rep to give the player per handoff
    },
    delivery = { -- Allow rep earnings in deliveries
        enabled = true, -- Enable or disable rep earnings in deliveries
        chance = 10, -- Chance in percentage, that'll give rep to the player each handoff
        amount = { min = 1, max = 10 }, -- Amount of rep to give the player per handoff
    },
},
```

***

## Creating A Contact

{% hint style="info" %}
Once you have configured that, now we want to create a contact for our new skill. You also have the option to just add the reputation items into an existing contact if you'd like. Here we'll add a new contact instead
{% endhint %}

```lua
{
    name = 'MannyOnBrazzers', -- Contacts Name, must be unique per contact. This is technically an identifier.
    description = 'A beautiful human being', -- Small bio about the contact
    image = './images/avatar1.png', -- Images are easy to add, chatGPT them if you'd like. Place them into the html/images folder and put the path here
    boost = 10, -- This is profit boost added to the sale of each delivery in percentage
    requirements = { -- Reputation requirement to get access to deliveries. You can add multiple requirements related to reputation, or you can remove requirements completely.
        { label = '100 MethReputation', reputation = 'meth', amount = 100 },
    },
    drugs = { -- Drugs accepted for this contacts delivery missions. There must be at least 1, but you can add multiple. This item must be in the items.lua data as well to retrieve the price and other information
        { label = 'Meth', item = 'meth' },
    },
    routes = {
        amount = { min = 2, max = 2 }, -- Amount of routes generated for this contact
        drugs = { min = 10, max = 25 }, -- Amount of drugs sold at each location
    },
    locations = { -- All the routes the ped gives for your deliveries
        vector4(-50.33, -1783.24, 28.3, 133.9),
        -- You can continue adding more locations as you like
    },
}
```

***

## Creating The Item

{% hint style="info" %}
Locate ox\_inventory/data/items.lua. We'll create our meth item
{% endhint %}

```lua
['meth'] = {
	label = 'Meth',
	weight = 10,
	stack = true,
	client = {
		image = 'meth.png',
	}
},
```

{% hint style="info" %}
Finally we want to make sure its an acceptable item in our drug system. Locate data/items.lua in the drugs table we insert this
{% endhint %}

```
meth= {
    model = 'xm3_prop_xm3_bag_coke_01a',
    price = { min = 400, max = 700 },
    amount = { restrict = true, max = 10 },
    negotiation = { min = 5, max = 20 },
},
```

{% hint style="danger" %}
Make sure to have `sqlUpdate` in data/main.lua set to true. This will auto update your SQL with your new skills and reputation with restarting your resource. You are now done.
{% endhint %}
