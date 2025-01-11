---
icon: code
---

# Config

## Main

```lua
return {
    debug = false, -- just debug mode for extra printing and zones
    sqlUpdate = true, -- set this to false if you haven't or don't plan on doing any changes to the config. This auto updates the sql with the skill changes, or reputation changes (adding/ removing)
    theme = 'orange', -- The options are 'blue', 'yellow', 'white', 'teal', 'pink'

    cornering = {
        cooldown = {
            enabled = false, -- Enable or disable cooldown per handoff
            time = 1, -- Time the cooldown should be in minutes
        },
        police = {
            minimum = 0, -- Minimum police required online to corner
            allow = false, -- Allow cops to corner also
            alert = {
                chance = 100, -- Chance that an alert goes off to police per handoff
            },
        },
        animations = { -- Animations for cornering
            handoff = { dict = 'mp_common', anim = 'givetake1_a' },
            pickup = { dict = 'weapons@holster_fat_2h', anim = 'holster' }
        },
        rob = { -- Allow the target to rob the player
            enabled = true, -- off/ on
            chance = 20, -- chance in percentage that the target robs the player
        },
        dialogue = { -- Dialog allows cops to speak with those who a player had sold to to recover a possible first name of the seller
            enabled = true, -- Enable/ disable
            chance = 25, -- Chance in percentage that a first name is revealed to the cop
            deny = { -- Deny dialog
                'Man, I don’t know what you’re talking about—must’ve been someone else, not me.',
                'You got the wrong guy, officer—I’m just out here minding my own business.',
                'I don’t know anything about that, and even if I did, I’m not saying a word',
                'Sales? I’m no businessman, officer—just trying to stay out of trouble.',
                'Unless you’ve got proof, I’m not about to incriminate myself for something I didn’t do.',
            },
            accept = { -- Accept dialog '%s' is where the players first name will go
                'Alright, fine, his name’s %s—but that’s all I’m saying.',
                'Yeah, I sold to %s, but I don’t know anything else about him.',
                'Look, it was %s, but you didn’t hear that from me.',
                'I’m not trying to cause problems, but the guy’s name was %s.',
                'Okay, okay, the buyer’s name was %s—now can we move on?',
            },
        },
        zones = {
            enabled = false, -- If enabled, this prevents players from selling absolutely anywhere they want
            game = { -- Game zones viewed from (https://docs.fivem.net/natives/?_0xCD90657D4C30E1CA)
                -- All of these zones allow all drugs to be sold at each one
                AIRP = false,
                ALTA = true,
                CHIL = false,
                CHU = false,
                CYPRE = false,
                DAVIS = false,
                DELSOL = false,
                GRAPES = false,
                HARMO = false,
                HAWICK = false,
                MIRR = false,
                PALETO = false,
                RICHM = false,
                ROCKF = false,
                SANDY = false,
                SLAB = false,
                STRAW = true,
                VCANA = false,
                VESP = false,
                VINE = false,
                WINDF = false,
                LOSPUER = true,
            },
            poly = { -- Poly of zones you would like to manually add
                {
                    label = 'Grove Street',
                    points = {
                        vec(130.03, -2026.09, 18.00),
                        vec(-152.0, -1785.92, 18.00),
                        vec(46.86, -1688.19, 18.00),
                        vec(248.25, -1863.51, 18.00),
                    },
                    items = { -- Items that can only be sold in this zone. If you leave it empty, players can sell any type of drug
                        'weed',
                    }
                },
            },
        },
    },

    delivery = {
        animations = { -- Animations for the delivery
            handoff = { dict = 'mp_common', anim = 'givetake1_a' },
            pickup = { dict = 'weapons@holster_fat_2h', anim = 'holster' }
        },
        blip = { -- Blip info for the delivery
            sprite = 351, color = 5, scale = 0.7,
            routeColor = 5,
        },
        police = {
            minimum = 5, -- Minimum police required online to deliveries
            allow = false, -- Allow cops to do deliveries
            alert = {
                chance = 0, -- Chance that an alert goes off to police per delivery
            },
        },
        cooldown = {
            enabled = true, -- Cooldown for each contact after canceling or completing (in minutes)
            time = 30, -- Time the cooldown should be in minutes
        },
    },

    commands = {
        enabled = true, -- If admin commands for adding/removing rep is enabled or not
    },

    peds = { -- List of peds for deliveries
        "ig_abigail",
        -- many more listed in the actual resour
    },
}
```

***

## Contacts

<pre class="language-lua"><code class="lang-lua">return {
    {
        name = 'Jerome Tyson', -- Contacts Name, must be unique per contact. This is technically an identifier.
        description = 'A gritty, street-savvy individual exuding confidence, embodying the high-stakes world of underground dealings.', -- Small bio about the contact
        image = './images/avatar1.png', -- Image can be a link or reference from the images folder
        boost = 10, -- This is profit boost added to the sale of each delivery in percentage
        requirements = { -- Reputation requirement to get access to deliveries. You can add multiple requirements related to reputation, or you can remove requirements completely.
            { label = '100 Weed Reputation', reputation = 'weed', amount = 100 },
        },
        drugs = { -- Drugs accepted for this contacts delivery missions. There must be at least 1, but you can add multiple. This item must be in the items.lua data as well to retrieve the price and other information
            { label = 'Weed', item = 'weed' },
        },
        routes = {
            amount = { min = 2, max = 2 }, -- Amount of routes generated for this contact
            drugs = { min = 10, max = 25 }, -- Amount of drugs sold at each location
        },
        locations = { -- All the routes the ped gives for your deliveries
            vector4(-50.33, -1783.24, 28.3, 133.9),
<strong>            -- many more listed in the actual resource
</strong>        },
    },
    {
        name = 'Rico "Snow" Alvarez',
        description = 'A smooth-talking street hustler with a knack for making deals, Rico is known for always having the purest product and a network that stretches across the city.',
        image = './images/avatar2.png',
        requirements = {
            { label = '100 Cocaine Reputation', reputation = 'cocaine', amount = 100 },
        },
        drugs = {
            { label = 'Cocaine', item = 'cocaine' },
        },
        routes = {
            amount = { min = 1, max = 2 },
            drugs = { min = 1, max = 10 },
        },
        locations = {
            vector4(-50.33, -1783.24, 28.3, 133.9),
            -- many more listed in the actual resource
        },
    },
}
</code></pre>

***

## Items

```lua
return {
    drugs = {
        weed = { -- Item name
            model = 'sf_prop_sf_bag_weed_open_01b', -- Model of the item for the handoff object
            price = { min = 200, max = 500 }, -- Minimum and maximum amount of money you can get from the drug.
            amount = { restrict = true, max = 10 }, -- If restricted, it retricts the max amount of drugs that can be cornered at a time. Highly recommended.
            negotiation = { min = 5, max = 20 }, -- Picks and random percentage between the min and max, if the negotiated price increases by that percentage its denies the negotation.
        },
        cocaine = {
            model = 'xm3_prop_xm3_bag_coke_01a',
            price = { min = 400, max = 700 },
            amount = { restrict = true, max = 10 },
            negotiation = { min = 5, max = 20 },
        },
    },
    cleaning = {
        chance = 100, -- Chance to clean items per delivery and cornering handoff
        items = {
            inked = { -- Item name
                price = { min = 100, max = 250 }, -- Minimum and maximum amount of money you can get from cleaning this item.
                amount = { restrict = true, max = 10 }, -- If restricted, it retricts the max amount of cleaning items that can be cleaned at a time. Highly recommended.
            },
        },
    },
}
```

***

## Market

```lua
return {
    pickup = { -- Pickup location after your purchase the items from your cart
        coords = vec(507.02, 3099.61, 41.31),
        poly = {
            vec(505.93, 3095.92, 41.55),
            vec(510.21, 3101.16, 41.55),
            vec(508.05, 3103.22, 41.47),
            vec(503.39, 3098.0, 41.32),
        },
    },
    expiration = {
        offer = 7, -- Expiration time in days that a listing will expire from the market
        history = 30, -- Expiration time in days that a sale history will remain in your history list
    },
    settings = {
        whitelist = { -- Whitelist will only allow these items to be sold on the marketplace
            enabled = true,
            items = {
                weed = true,
                cocaine = true,
            },
        },
        blacklist = { -- Blacklist will only allow items in but these listed below
            enabled = false,
            items = {},
        },
        price = { -- Price allows you to set the absolute maximum price an item can be posted for
            weed = 250,
        },
    },
}
```

***

## Reputation

```lua
return {
    {
        label = 'Weed', -- Label for the reputation
        icon = 'fa-solid fa-cannabis', -- Icon associated with this reputation.
        identifier = 'weed', -- Used to identify the rep, add/remove rep. Main string in the db
        items = { -- List of items that can increase the reputation when sold
            'weed',
            'joints',
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
    {
        label = 'Cocaine',
        icon = 'fa-solid fa-seedling',
        identifier = 'cocaine',
        items = {
            'cocaine',
        },
        cornering = {
            enabled = true,
            chance = 10,
            amount = { min = 1, max = 5 },
        },
        delivery = {
            enabled = true,
            chance = 10,
            amount = { min = 1, max = 10 },
        },
    },
}
```

***

## Skills

```lua
return {
    {
        label = 'Weed', -- Label of the specialization
        identifier = 'weed', -- This identifier should match a rep identifier
        skills = {
            {
                label = 'Green Thumb', -- Label of the skill (should be unique and different for each skill)
                description = 'Learn the basics of cultivation, slightly increasing yield from your crops.', -- Description of the skill
                icon = 'fa-solid fa-seedling', -- Icon for the skill in the menu
                requirements = { -- Requirements to unlock the skill
                    { label = '25 Weed Reputation', reputation = 'weed', value = 25 },
                },
                rewards = { -- List of rewards for unlocking the skill (See DOCS to see the available options or add your own)
                    { type = 'money', money = 'cash', amount = 500 },
                    { type = 'item', item = 'lockpick', amount = 1, metadata = {} },
                    { type = 'reputation', rep = 'weed', amount = 10 },
                },
                row = 1, -- What row should the skill be on
            },
            {
                label = 'Streetwise',
                description = 'Decrease the chances of being caught during low-profile deals.',
                icon = 'fa-solid fa-city',
                requirements = {
                    { label = '100 Weed Reputation', reputation = 'weed', value = 100 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 550 },
                },
                row = 2,
            },
            {
                label = 'Negotiator',
                description = 'Unlock the ability to negotiate better bulk deals with suppliers.',
                icon = 'fa-solid fa-comments',
                requirements = {
                    { label = '150 Weed Reputation', reputation = 'weed', value = 150 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 600 },
                },
                row = 2,
            },
            {
                label = 'Bulk Carrier',
                description = 'Increase your carrying capacity further for large operations.',
                icon = 'fa-solid fa-truck',
                requirements = {
                    { label = '250 Weed Reputation', reputation = 'weed', value = 250 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 700 },
                },
                row = 2,
            },
            {
                label = 'Fast Talker',
                description = 'Talk your way out of trouble if caught during a deal.',
                icon = 'fa-solid fa-comment-dots',
                requirements = {
                    { label = '300 Weed Reputation', reputation = 'weed', value = 300 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 1000 },
                },
                row = 2,
            },
            {
                label = 'Master Grower',
                description = 'Master the art of cultivation, significantly increasing crop yields.',
                icon = 'fa-solid fa-tractor',
                requirements = {
                    { label = '400 Weed Reputation', reputation = 'weed', value = 400 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 1500 },
                },
                row = 3,
            },
            {
                label = 'Trusted Supplier',
                description = 'Gain access to exclusive, high-value clients who pay top dollar.',
                icon = 'fa-solid fa-user-tie',
                requirements = {
                    { label = '450 Weed Reputation', reputation = 'weed', value = 450 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 1750 },
                },
                row = 3,
            },
            {
                label = 'Safe Routes',
                description = 'Discover safer delivery routes, drastically reducing risk during drop-offs.',
                icon = 'fa-solid fa-road',
                requirements = {
                    { label = '500 Weed Reputation', reputation = 'weed', value = 500 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 2000 },
                },
                row = 3,
            },
            {
                label = 'Silent Packager',
                description = 'Package goods faster without leaving traces of evidence.',
                icon = 'fa-solid fa-box-open',
                requirements = {
                    { label = '550 Weed Reputation', reputation = 'weed', value = 550 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 2250 },
                },
                row = 3,
            },
            {
                label = 'Networker',
                description = 'Expand your dealer network, unlocking the ability to hire runners.',
                icon = 'fa-solid fa-network-wired',
                requirements = {
                    { label = '600 Weed Reputation', reputation = 'weed', value = 600 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 2250 },
                },
                row = 3,
            },
            {
                label = 'Indoor Cultivator',
                description = 'Unlock the ability to grow indoors, making operations more discreet.',
                icon = 'fa-solid fa-house',
                requirements = {
                    { label = '750 Weed Reputation', reputation = 'weed', value = 750 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 3000 },
                },
                row = 4,
            },
            {
                label = 'Hybrid Master',
                description = 'Create hybrid strains with unique effects, attracting high-end buyers.',
                icon = 'fa-solid fa-dna',
                requirements = {
                    { label = '850 Weed Reputation', reputation = 'weed', value = 850 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 4000 },
                },
                row = 4,
            },
            {
                label = 'Businessman',
                description = 'Establish a legal front, laundering profits seamlessly.',
                icon = 'fa-solid fa-chart-line',
                requirements = {
                    { label = '950 Weed Reputation', reputation = 'weed', value = 950 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 5000 },
                },
                row = 4,
            },
            {
                label = 'Gang Ties',
                description = 'Form alliances with gangs for protection and expanded territory.',
                icon = 'fa-solid fa-skull-crossbones',
                requirements = {
                    { label = '1100 Weed Reputation', reputation = 'weed', value = 1100 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 6000 },
                },
                row = 4,
            },
            {
                label = 'Empire Builder',
                description = 'Gain the ability to automate aspects of your operation, turning it into an empire.',
                icon = 'fa-solid fa-building',
                requirements = {
                    { label = '1250 Weed Reputation', reputation = 'weed', value = 1250 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 7000 },
                },
                row = 5,
            },
            {
                label = 'Efficient Cultivator',
                description = 'Optimize your crops, reducing resource usage while maintaining yield.',
                icon = 'fa-solid fa-recycle',
                requirements = {
                    { label = '1350 Weed Reputation', reputation = 'weed', value = 1350 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 7500 },
                },
                row = 5,
            },
            {
                label = 'Greenhouse Pro',
                description = 'Maximize indoor growth potential with advanced greenhouse techniques.',
                icon = 'fa-solid fa-leaf',
                requirements = {
                    { label = '1450 Weed Reputation', reputation = 'weed', value = 1450 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 8000 },
                },
                row = 5,
            },
            {
                label = 'Luxury Branding',
                description = 'Package and market your product as a premium brand.',
                icon = 'fa-solid fa-gem',
                requirements = {
                    { label = '1600 Weed Reputation', reputation = 'weed', value = 1600 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 9000 },
                },
                row = 6,
            },
            {
                label = 'Exotic Strains',
                description = 'Develop unique strains that attract exclusive buyers.',
                icon = 'fa-solid fa-vial',
                requirements = {
                    { label = '1800 Weed Reputation', reputation = 'weed', value = 1800 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 10000 },
                },
                row = 6,
            },
            {
                label = 'Global Expansion',
                description = 'Expand operations globally, dominating the international market.',
                icon = 'fa-solid fa-globe',
                requirements = {
                    { label = '2000 Weed Reputation', reputation = 'weed', value = 2000 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 12000 },
                },
                row = 7,
            },
        },
    },
    {
        label = 'Cocaine', -- Label of the specialization
        identifier = 'cocaine', -- This identifier should match a rep identifier
        skills = {
            {
                label = 'Quick Cut',
                description = 'Learn the basics of cutting cocaine, slightly increasing its purity.',
                icon = 'fa-solid fa-scissors',
                requirements = {
                    { label = '25 Cocaine Reputation', reputation = 'cocaine', value = 25 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 1000 },
                },
                row = 1,
            },
            {
                label = 'Street Smarts',
                description = 'Reduce the chance of detection during low-profile cocaine deals.',
                icon = 'fa-solid fa-user-secret',
                requirements = {
                    { label = '100 Cocaine Reputation', reputation = 'cocaine', value = 100 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 1250 },
                },
                row = 2,
            },
            {
                label = 'Efficient Packager',
                description = 'Package cocaine more efficiently, reducing waste and saving time.',
                icon = 'fa-solid fa-boxes-stacked',
                requirements = {
                    { label = '150 Cocaine Reputation', reputation = 'cocaine', value = 150 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 1500 },
                },
                row = 2,
            },
            {
                label = 'High Roller Deals',
                description = 'Unlock access to high-value buyers for bulk cocaine deals.',
                icon = 'fa-solid fa-money-bill-wave',
                requirements = {
                    { label = '250 Cocaine Reputation', reputation = 'cocaine', value = 250 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 2000 },
                },
                row = 2,
            },
            {
                label = 'Silent Transporter',
                description = 'Learn how to conceal shipments, reducing detection risks during transportation.',
                icon = 'fa-solid fa-truck-loading',
                requirements = {
                    { label = '300 Cocaine Reputation', reputation = 'cocaine', value = 300 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 2500 },
                },
                row = 3,
            },
            {
                label = 'Pure Perfection',
                description = 'Master the art of purifying cocaine, increasing its value.',
                icon = 'fa-solid fa-flask',
                requirements = {
                    { label = '400 Cocaine Reputation', reputation = 'cocaine', value = 400 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 3000 },
                },
                row = 3,
            },
            {
                label = 'Trusted Supplier',
                description = 'Build a reputation with clients, earning better prices for your product.',
                icon = 'fa-solid fa-user-tie',
                requirements = {
                    { label = '500 Cocaine Reputation', reputation = 'cocaine', value = 500 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 3500 },
                },
                row = 3,
            },
            {
                label = 'Smuggling Routes',
                description = 'Gain knowledge of safe smuggling routes to move large quantities.',
                icon = 'fa-solid fa-map',
                requirements = {
                    { label = '600 Cocaine Reputation', reputation = 'cocaine', value = 600 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 4000 },
                },
                row = 3,
            },
            {
                label = 'High-End Packaging',
                description = 'Use premium packaging to increase the market value of your cocaine.',
                icon = 'fa-solid fa-box-open',
                requirements = {
                    { label = '700 Cocaine Reputation', reputation = 'cocaine', value = 700 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 4500 },
                },
                row = 4,
            },
            {
                label = 'Cartel Connections',
                description = 'Form alliances with cartels for increased distribution and territory.',
                icon = 'fa-solid fa-users',
                requirements = {
                    { label = '850 Cocaine Reputation', reputation = 'cocaine', value = 850 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 5000 },
                },
                row = 4,
            },
            {
                label = 'Empire Expansion',
                description = 'Automate key aspects of your operation, increasing efficiency and profits.',
                icon = 'fa-solid fa-industry',
                requirements = {
                    { label = '1000 Cocaine Reputation', reputation = 'cocaine', value = 1000 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 6000 },
                },
                row = 5,
            },
            {
                label = 'Effortless Concealment',
                description = 'Reduce the risk of shipments being discovered by authorities.',
                icon = 'fa-solid fa-mask',
                requirements = {
                    { label = '1200 Cocaine Reputation', reputation = 'cocaine', value = 1200 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 6500 },
                },
                row = 5,
            },
            {
                label = 'Fleet Management',
                description = 'Manage a fleet of transport vehicles for larger-scale operations.',
                icon = 'fa-solid fa-truck',
                requirements = {
                    { label = '1400 Cocaine Reputation', reputation = 'cocaine', value = 1400 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 7000 },
                },
                row = 5,
            },
            {
                label = 'Stealth Master',
                description = 'Significantly decrease the likelihood of being detected during operations.',
                icon = 'fa-solid fa-user-ninja',
                requirements = {
                    { label = '1600 Cocaine Reputation', reputation = 'cocaine', value = 1600 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 7500 },
                },
                row = 5,
            },
            {
                label = 'Private Jet Access',
                description = 'Gain access to private jets for faster and safer transportation.',
                icon = 'fa-solid fa-plane',
                requirements = {
                    { label = '1800 Cocaine Reputation', reputation = 'cocaine', value = 1800 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 8000 },
                },
                row = 5,
            },
            {
                label = 'Luxury Dealer',
                description = 'Expand your clientele to include wealthy individuals, increasing profit margins.',
                icon = 'fa-solid fa-gem',
                requirements = {
                    { label = '2000 Cocaine Reputation', reputation = 'cocaine', value = 2000 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 8500 },
                },
                row = 6,
            },
            {
                label = 'Underground Lab',
                description = 'Unlock a hidden lab to process larger quantities of cocaine at once.',
                icon = 'fa-solid fa-flask-vial',
                requirements = {
                    { label = '2200 Cocaine Reputation', reputation = 'cocaine', value = 2200 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 9000 },
                },
                row = 6,
            },
            {
                label = 'Global Distribution',
                description = 'Expand operations internationally, increasing potential profits exponentially.',
                icon = 'fa-solid fa-globe',
                requirements = {
                    { label = '2500 Cocaine Reputation', reputation = 'cocaine', value = 2500 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 10000 },
                },
                row = 6,
            },
            {
                label = 'Elite Clientele',
                description = 'Gain access to exclusive clients who pay top dollar for premium products.',
                icon = 'fa-solid fa-crown',
                requirements = {
                    { label = '3000 Cocaine Reputation', reputation = 'cocaine', value = 3000 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 12000 },
                },
                row = 7,
            },
            {
                label = 'Kingpin Status',
                description = 'Reach the pinnacle of the cocaine trade, automating all aspects of your empire.',
                icon = 'fa-solid fa-chess-king',
                requirements = {
                    { label = '3500 Cocaine Reputation', reputation = 'cocaine', value = 3500 },
                },
                rewards = {
                    { type = 'money', money = 'cash', amount = 15000 },
                },
                row = 8,
            },
        }
        
    },
}
```

***
