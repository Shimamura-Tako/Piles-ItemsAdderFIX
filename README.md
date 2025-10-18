# Piles-ItemsAdderFIX
Make your Piles resourcepack no longer conflict with ItemsAdder.

[中文文档](README_zhcn.md)

## What is this?
This magical² extension allows your Piles resourcepack to no longer conflict with your ItemsAdder item textures, and also works with other resource packs that use IA (such as the Slimefun resourcepack).

## How to use?
0. Download this repository and extract it on your server host

1. Place the `pilesfix` folder in the `contents` directory, execute `/iareload` and `/iazip`, then load the `generated.zip` resourcepack

2. Modify the Piles resourcepack by deleting all files in the `assets/minecraft/items` directory, then load it in the game above `generated.zip`

3. That's it! Now you can use Piles normally without worrying about conflicts with ItemsAdder resources

4. It is recommended to use BungeeResourcepacks or other plugins to send resource packs to players in the correct order.

## Why are the potion bottles I placed turning blue?
You need to remove the `tints` values for the pilesfix entries in `generated.zip -> ia_overlay_1_21_6_plus/assets/minecraft/items/potion.json`. Here's a reference example: [potion.json](potion.json)

If you don't frequently create potion-related content, you can place the modified potion.json back into the `assets/minecraft/items` directory of the Piles resource pack, keeping that resource pack above `generated.zip`.

This way, you'll only need to modify potion.json when creating new potion-related content, rather than having to repeat the modification every time you run `/iazip`.

I'm not sure if there's a better solution, but that would require mastery of ItemsAdder - and I'm just a *noob*, * *bruh* *.

## I'm encountering an issue!
Please submit an issue in this repository instead of going to Piles's repository, because this extension was created by me, not by Athlaeos.

## Why am I having issues using it on versions below 1.21.4?
This extension was initially created for my own server, which runs on version 1.21.8.

Therefore, you might encounter some minor problems when using it on older server versions.

However, if you really need it for lower versions, try using DeepSeek, ChatGPT, or other AI tools to help you create a compatible version for lower Minecraft versions.

*If Athlaeos provides me with a copy of Valhalla Premium to encourage me to continue development, I will dedicate time in the future to personally test and ensure compatibility with older Minecraft server versions.*

## Future Plans
- Make potion bottles no longer turn entirely blue
