
# [简易教程] 如何添加物品 和 NPC

## 一、操作数据库的工具

首先需要准备一个数据库管理工具，常见的有 Navicat 或者 Sqlyog。

百度然后下载一个就行，安装以后连接到你的数据库，一般需要你的 ip、用户名、密码、端口号（默认3306）。这一步不会请自行百度。

如果顺利，登录数据库以后，你会看到三个库，选择 mangos，不用管 characters 和 realmd 。

## 二、添加物品

在 mangos 库中，有很多表，添加物品我们只用到 item_template 表。

这个表中大约有数万条记录，每一条记录代表一个物品。

我先把例子放上来，下面这个是一个自定义物品的完整数据：

```sql
insert into `item_template` (`entry`, `class`, `subclass`, `name`, `displayid`, `Quality`, `Flags`, `BuyCount`, `BuyPrice`, `SellPrice`, `InventoryType`, `AllowableClass`, `AllowableRace`, `ItemLevel`, `RequiredLevel`, `RequiredSkill`, `RequiredSkillRank`, `requiredspell`, `requiredhonorrank`, `RequiredCityRank`, `RequiredReputationFaction`, `RequiredReputationRank`, `maxcount`, `stackable`, `ContainerSlots`, `stat_type1`, `stat_value1`, `stat_type2`, `stat_value2`, `stat_type3`, `stat_value3`, `stat_type4`, `stat_value4`, `stat_type5`, `stat_value5`, `stat_type6`, `stat_value6`, `stat_type7`, `stat_value7`, `stat_type8`, `stat_value8`, `stat_type9`, `stat_value9`, `stat_type10`, `stat_value10`, `dmg_min1`, `dmg_max1`, `dmg_type1`, `dmg_min2`, `dmg_max2`, `dmg_type2`, `dmg_min3`, `dmg_max3`, `dmg_type3`, `dmg_min4`, `dmg_max4`, `dmg_type4`, `dmg_min5`, `dmg_max5`, `dmg_type5`, `armor`, `holy_res`, `fire_res`, `nature_res`, `frost_res`, `shadow_res`, `arcane_res`, `delay`, `ammo_type`, `RangedModRange`, `spellid_1`, `spelltrigger_1`, `spellcharges_1`, `spellppmRate_1`, `spellcooldown_1`, `spellcategory_1`, `spellcategorycooldown_1`, `spellid_2`, `spelltrigger_2`, `spellcharges_2`, `spellppmRate_2`, `spellcooldown_2`, `spellcategory_2`, `spellcategorycooldown_2`, `spellid_3`, `spelltrigger_3`, `spellcharges_3`, `spellppmRate_3`, `spellcooldown_3`, `spellcategory_3`, `spellcategorycooldown_3`, `spellid_4`, `spelltrigger_4`, `spellcharges_4`, `spellppmRate_4`, `spellcooldown_4`, `spellcategory_4`, `spellcategorycooldown_4`, `spellid_5`, `spelltrigger_5`, `spellcharges_5`, `spellppmRate_5`, `spellcooldown_5`, `spellcategory_5`, `spellcategorycooldown_5`, `bonding`, `description`, `PageText`, `LanguageID`, `PageMaterial`, `startquest`, `lockid`, `Material`, `sheath`, `RandomProperty`, `block`, `itemset`, `MaxDurability`, `area`, `Map`, `BagFamily`, `ScriptName`, `DisenchantID`, `FoodType`, `minMoneyLoot`, `maxMoneyLoot`, `Duration`, `ExtraFlags`) values ('30000','12','0','十年勋章','35141','4','2048','1','0','0','0','-1','-1','86','0','0','0','0','0','0','0','0','0','100','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','0','-1','0','-1','0','0','0','0','-1','0','-1','0','0','0','0','-1','0','-1','0','0','0','0','-1','0','-1','0','0','0','0','-1','0','-1','4','用于兑换职业套装。','0','0','0','0','0','1','0','0','0','0','0','0','0','0','','0','0','0','0','0','0');
```

看到这些不用懵，你不必了解全部。

每一条记录都有几个最重要的部分，比如：entry、class、subclass、name、displayid、quanlity 等等，我一一说明。

**entry**

物品ID，不允许与其它物品重复

**class**

物品类型，有以下这些值。

```bash
ID        Name
0        Consumable
1        容器
2        武器
3        Gem
4        护甲
5        Reagent
6        Projectile
7        商品
8        Generic(OBSOLETE)
9        Recipe
10        Money(OBSOLETE)
11        Quiver
12        任务物品
13        钥匙
14        Permanent(OBSOLETE)
15        杂物
16        Glyph
```

**subclass**

物品子类型。

```bash
Class   ID        Subclass ID       Subclass Name        Comments
0        0        Consumable        Usability in combat is decided by the spell assigned.
0        1        Potion
0        2        Elixir
0        3        Flask
0        4        Scroll
0        5        Food & Drink
0        6        Item Enhancement
0        7        Bandage
0        8        Other
1        0        Bag
1        1        Soul Bag
1        2        Herb Bag
1        3        Enchanting Bag
1        4        Engineering Bag
1        5        Gem Bag
1        6        Mining Bag
1        7        Leatherworking Bag
2        0        Axe        One handed
2        1        Axe        Two handed
2        2        Bow
2        3        Gun
2        4        Mace        One handed
2        5        Mace        Two handed
2        6        Polearm
2        7        Sword        One handed
2        8        Sword        Two handed
2        9        Obsolete
2        10        Staff
2        11        Exotic
2        12        Exotic
2        13        Fist Weapon
2        14        Miscellaneous        (Blacksmith Hammer, Mining Pick, etc.)
2        15        Dagger
2        16        Thrown
2        17        Spear
2        18        Crossbow
2        19        Wand
2        20        Fishing Pole
3        0        Red
3        1        Blue
3        2        Yellow
3        3        Purple
3        4        Green
3        5        Orange
3        6        Meta
3        7        Simple
3        8        Prismatic
4        0        Miscellaneous
4        1        Cloth
4        2        Leather
4        3        Mail
4        4        Plate
4        5        Buckler(OBSOLETE)
4        6        Shield
4        7        Libram
4        8        Idol
4        9        Totem
5        0        Reagent
6        0        Wand(OBSOLETE)
6        1        Bolt(OBSOLETE)
6        2        Arrow
6        3        Bullet
6        4        Thrown(OBSOLETE)
7        0        Trade Goods
7        1        Parts
7        2        Explosives
7        3        Devices
7        4        Jewelcrafting
7        5        Cloth
7        6        Leather
7        7        Metal & Stone
7        8        Meat
7        9        Herb
7        10        Elemental
7        11        Other
7        12        Enchanting
8        0        Generic(OBSOLETE)
9        0        Book
9        1        Leatherworking
9        2        Tailoring
9        3        Engineering
9        4        Blacksmithing
9        5        Cooking
9        6        Alchemy
9        7        First Aid
9        8        Enchanting
9        9        Fishing
9        10        Jewelcrafting
10        0        Money(OBSOLETE)
11        0        Quiver(OBSOLETE)
11        1        Quiver(OBSOLETE)
11        2        Quiver        Can hold arrows
11        3        Ammo Pouch        Can hold bullets
12        0        Quest
13        0        Key
13        1        Lockpick
14        0        Permanent
15        0        Junk
15        1        Reagent
15        2        Pet
15        3        Holiday
15        4        Other
15        5        Mount
16        1        Warrior
16        2        Paladin
16        3        Hunter
16        4        Rogue
16        5        Priest
16        6        Death Knight
16        7        Shaman
16        8        Mage
16        9        Warlock
16        11       Druid
```

**name**

物品名称。

**displayid**

物品对应模型的ID。

**Quality**

物品品质：

```bash
ID       Color       Quality
0        灰色
1        白色        Common
2        绿色        Uncommon
3        蓝色        Rare
4        紫色        Epic
5        橙色        Legendary
6        红色        Artifact
```

**BuyPrice**

物品在商店里的售价。

**SellPrice**

物品卖给商店的价格。

**InventoryType**

物品可以被装备在哪个装备栏：

```bash
ID        Slot Name
0        不可装备
1        头
2        项链
3        肩膀
4        衬衣
5        胸部
6        腰
7        腿
8        脚
9        护腕
10        手套
11        手指
12        饰品
13        武器
14        盾牌
15        Ranged
16        背部
17        双手武器
18        背包
19        Tabard
20        Robe
21        Main hand
22        Off hand
23        Holdable (Tome)
24        Ammo
25        Thrown
26        Ranged right
27        Quiver
28        Relic
```

**ItemLevel**

物品等级。

**RequiredLevel**

能够使用该物品的人物等级。

**requiredhonorrank**

能够使用该物品的军衔等级。

**maxcount**

一个玩家可以拥有的最大值，0 代表没有上限。

**stackable**

是否可叠加。

**ContainerSlots**

如果物品是个背包，拥有多少个格子。

**bonding**

物品绑定方式。

```bash
ID       Bonding Type
1        拾取后绑定
2        装备后绑定
3        使用后绑定
4        任务物品
```

**description**

物品描述信息。

-------------------------------------------------------

以上这些就是物品最主要的属性，按照规则修改即可。

小技巧：如果不知道怎么改，最好的办法是找一个差不多的物品，照着样子改。比如你想加一把新的单手剑，那就把风剑找到（entry 19019），照着它改就简单多了（entry 不能重复）。

## 三、添加 NPC

添加 NPC 需要修改两个表：creature 和 creature_template。

creature 表：

* guid：唯一id

* id：与creature_template 的 entry 一致

* map：地图id

* odelid：人物模型id

* equipment_id：人物装备模型id

------------------------------------------------------

creature_template 表：

* entry：唯一id

* name：名字

* FactionAlliance：对于联盟玩家的阵营

* FactionHorde：对于部落玩家的阵营

* Scale：模型缩放比例

* Family：野兽类型

* NpcFlags：NPC 类型

    比如一个商人 NPC，他的值应该是 128。

    EXAMPLE:

    So If You Want An NPC That Is a Quest Giver, a Vendor And Can Also Repair You Just Add The Specific Flags Together:

    1 + 2 + 128 + 4096 = 4227.
    NpcFlags = 4227

* Rank

    ```bash
    Rank        Name
    0        Normal
    1        Elite
    2        Rare Elite
    3        World Boss
    4        Rare
    ```

------------------------------------------------------

## 四、让 NPC 出售指定物品

比如你新增了一个物品，entry 是 30000；同时新增了一个 NPC，entry 是 90000。
你想让这个新 NPC 90000 出售新物品 30000。

```sql
insert into `npc_vendor` (`entry`, `item`) values('30000','90000');
```

很简单，在 npc_vendor 表里增加一条数据即可。不过切记这个 NPC 必须是个商人（即这个 npc 在 creature_tempalte 表的 NPCFlags 字段是 128）。

npc_vendor 表的一条数据代表一个可出售的商品：

* entry：是 npc 的 entry（creature_template 的 entry）
* item：是物品的 entry（item_template 的 entry）
* maxcount（出售上限）、incrtime（刷新时间）、condition_id（刷新条件）三项可以无视，用默认值 0 就好。

每在某个 NPC 出售某件物品，都需要在这里加上一条记录。
