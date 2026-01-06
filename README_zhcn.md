# Piles-ItemsAdderFIX
让你的Piles资源包不再与ItemsAdder冲突。

[[English README]](README.md)

## 这是什么？
这个神奇²的扩展可以让你的Piles资源包不再与你的ItemsAdder物品纹理冲突，也对其他使用IA的资源包生效（例如Slimefun资源包）

如果你使用[ValhallaMMO-ItemsAdderFIX](https://github.com/Shimamura-Tako/ValhallaMMO-ItemsAdderFIX)的话，也与ValhallaMMO和ValhallaTrinkets兼容。

**目前，该扩展不支持1.21.11，因为ItemsAdder未更新支持，这不是我的问题。**
## 怎么使用？
0. 下载这个储存库并解压在你的服务器主机上

1. 将`pilesfix`文件夹放置在contents目录下，执行`/iareload`和`/iazip`并加载`generated.zip`资源包

2. 两种方法二选一：

- 从储存库根目录中获取正确版本的修改过后的资源包，并将其加载在游戏中，置于`generated.zip`之上 **(推荐)**

- **或者**修改Piles资源包，删除压缩包中`assets/minecraft/items`*目录下的所有文件，并将其加载在游戏中，置于`generated.zip`之上

- - (*: 在1.21.3及以下的版本里是`assets/minecraft/models/item/*.json`，并且不要删除同目录下其他文件夹的内容)

3. 完事！现在你可以正常使用Piles，而无需担心它会与ItemsAdder资源冲突

4. 建议使用BungeeResourcepacks或其他插件将资源包按正确的顺序发送给玩家

## 为什么我放下的药水瓶有一层奇怪的蓝色？
这里有两种可行的方法修复这个问题：

### 新方法
停止你的服务器，将 `contents/pilesfix/config/potion.yml` 的内容替换为[**potion_fixed.yml**](potion_fixed.yml) **（来自储存库根目录）** 的内容，然后按照下面的例子修改 `plugins/Piles/piletypes.json` 的药水小摆件部分：
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
之后，启动服务器，放下新的药水小摆件，你会看到它拥有正确的颜色。旧的药水小摆件需要拆除并重新摆放以便修复颜色。

其原理是将显示物品的类型从`POTION`修改为`GLASS_BOTTLE`，避免了药水的染色层；同时修改`CustomModelData`防止其与原本的玻璃瓶小摆件冲突。

### 旧方法
你需要将`generated.zip -> ia_overlay_1_21_6_plus/asstes/minecraft/items/potion.json`中关于pilesfix的项目的`tints`值删掉。这里提供一个参考示例：[potion.json](potion.json)

如果你不经常创建与药水相关的内容，你可以将修改过的`potion.json`放回Piles资源包的`assets/minecraft/items`目录下，保持该资源包位于`generated.zip`之上。

这样就可以只在新建药水有关内容时再修改`potion.json`，而不是每次`/iazip`都要重复修改。

### *第三种方法？*
或许还有[第三种方法](https://itemsadder.devs.beer/plugin-usage/adding-content/colored-models?q=tint#id-6.-set-the-specific-color-attribute-in-your-.yml-file)，但ItemsAdder似乎存在bug，导致无法用1.21.4以前的格式正确地修改药水染色层（IA 1.21.4+ 格式使用`ItemModel`而不是`CustomModelData`）。

## 我遇到了问题！
请在此储存库下提交issue，而不是跑去Piles的储存库，因为这个扩展是由我创建的，而不是Athlaeos。

## 将来的计划
- ~让药水瓶不再整体变蓝~ 2026/01/06 (修了一半)
- ~在旧版服务器上测试~ 不用改了
