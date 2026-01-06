# Piles-ItemsAdderFIX
Make your Piles resourcepack no longer conflict with ItemsAdder.

[[中文文档]](README_zhcn.md)

## What is this?
This magical² extension allows your Piles resourcepack to no longer conflict with your ItemsAdder item textures, and also works with other resource packs that use IA (such as the Slimefun resourcepack).

Compatible with ValhallaMMO (Free/Premium) and ValhallaTrinkets if you're using [ValhallaMMO-ItemsAdderFIX](https://github.com/Shimamura-Tako/ValhallaMMO-ItemsAdderFIX).

**Currently, this extension does not support version 1.21.11 because ItemsAdder hasn't been updated to support it yet. this is not an issue on my end.**
## How to use?
0. Download this repository and extract it on your server host

1. Place the `pilesfix` folder in the `contents` directory, execute `/iareload` and `/iazip`, then load the `generated.zip` resourcepack

2. Choose one of the two methods:

- Get the correctly versioned and modified resource pack from the repository's root directory, then load it in the game above `generated.zip` **(RECOMMENDED)**

- **OR** Modify the Piles resource pack by deleting all files in the `assets/minecraft/items`* directory, then load it in the game above `generated.zip`

- - (*: In versions 1.21.3 and below, it's `assets/minecraft/models/item/*.json` and do not delete the contents of other folders in the same directory)

3. That's it! Now you can use Piles normally without worrying about conflicts with ItemsAdder resources

4. It is recommended to use BungeeResourcepacks or other plugins to send resource packs to players in the correct order.

## Why are the potion bottles I placed turning blue?
There are two viable methods to fix this issue:
### New Method
Stop your server, and replace the content of `contents/pilesfix/config/potion.yml` with the content of [**potion_fixed.yml**](potion_fixed.yml) **from the repository's root directory**, then modify the potion piles section in `plugins/Piles/piletypes.json` according to the example below:
```
  {
    "MOD_TYPE": "me.athlaeos.piles.piles.SimplePile",
    "DATA": {
      "pileItem": "POTION",
      "type": "potions",
      "maxSize": 4,
      "displayItem": "GLASS_BOTTLE",
      "customModelData": [
        1882700,
        1882701,
        1882702,
        1882703
      ],
      "solid": false,
      "placementSound": "BLOCK_AMETHYST_BLOCK_PLACE",
      "takeSound": "BLOCK_AMETHYST_BLOCK_CHIME",
      "destroySound": "BLOCK_AMETHYST_BLOCK_BREAK"
    }
  },
```
After that, start the server and place new potion piles, you'll see they have the correct colors.

Old potion piles need to be removed and replaced to fix their colors.

The principle involves changing the displayed item type from `POTION` to `GLASS_BOTTLE`, avoiding the potion's tint layer, while modifying the `CustomModelData` to prevent conflicts with the original glass bottle piles.
### Old Method
You need to remove the `tints` values for the pilesfix entries in `generated.zip -> ia_overlay_1_21_6_plus/assets/minecraft/items/potion.json`. Here's a reference example: [potion.json](potion.json)

If you don't frequently create potion-related content, you can place the modified potion.json back into the `assets/minecraft/items` directory of the Piles resource pack, keeping that resource pack above `generated.zip`.

This way, you'll only need to modify potion.json when creating new potion-related content, rather than having to repeat the modification every time you run `/iazip`.

### *Third Method?*
There might be a [third method](https://itemsadder.devs.beer/plugin-usage/adding-content/colored-models?q=tint#id-6.-set-the-specific-color-attribute-in-your-.yml-file), but ItemsAdder seems to have a bug that prevents proper modification of potion tints in pre-1.21.4 formats (IA 1.21.4+ formats use `ItemModel` instead `CustomModelData`).

## I'm encountering an issue!
Please submit an issue in this repository instead of going to Piles's repository, because this extension was created by me, not by Athlaeos.

## Future Plans
- ~Make potion bottles no longer turn entirely blue~ 01/06/26 (consider it half-solved lol)
- ~Test it on older server versions~ It works nicely
