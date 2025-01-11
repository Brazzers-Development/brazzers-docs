---
icon: gear
---

# Installation

Welcome to the Drug Sales & Market installation guide! In this guide, you'll find step-by-step instructions to help you seamlessly install our asset. By carefully following each step, you can ensure a smooth and trouble-free installation process, provided the documentation is followed in its entirety.

{% hint style="danger" %}
If you lack programming experience, we strongly recommend reading each step thoroughly without skipping any lines, as every part of the documentation is essential and should not be overlooked. Alternatively, if you have a trusted developer, they can install the asset quickly, easily, and securely by carefully following this documentation step by step.
{% endhint %}

{% hint style="info" %}
If you encounter any issues after completing this documentation, we recommend reviewing each step carefully once again. After ensuring everything has been followed correctly, you can explore the **Common Errors** section within this documentation for additional information on frequent errors and troubleshooting tips to resolve issues independently.
{% endhint %}

## Asset Download

{% hint style="danger" %}
To access the asset, you must have completed the purchase using your own Keymaster account. If not, you can utilize the transfer system to move the asset to another Keymaster account.
{% endhint %}

{% hint style="success" %}
If you need to update the asset, you must repeat this step. Simply download the asset again, and you will receive the complete updated version.
{% endhint %}

You have reference the [Information](../../) section of [Paid Resources](broken-reference) for more information on downloading your asset.

***

## Asset Dependencies

{% hint style="warning" %}
Ensure the assets are correctly positioned by following this step carefully. Skipping it may result in errors, such as "exports not found." To avoid issues, do not overlook this crucial step.
{% endhint %}

```lua
-- Dependencies
ensure ox_lib
ensure ox_target
ensure ox_inventory
ensure Renewed-Lib

-- Our Resource
ensure brazzers_sales
```

***

## SQL Installation

{% hint style="info" %}
Our resouce auto creates the neccessary tables, but if you decide to do it manually, simply run the provided sql file in the resource.
{% endhint %}

***

## Item Installation

{% hint style="info" %}
Head over to ox\_inventory/data/weapons.lua and paste the following item
{% endhint %}

{% hint style="warning" %}
Locate the image for the item in brazzers\_radar/images and drag and drop that into ox\_inventory/web/images if you need an item image.
{% endhint %}

```lua
['trapbook'] = {
	label = 'Trap Book',
	weight = 500,
	stack = false,
	client = {
		export = 'brazzers_sales.trapbook',
		image = 'trapbook.png',
	}
},
```

***
