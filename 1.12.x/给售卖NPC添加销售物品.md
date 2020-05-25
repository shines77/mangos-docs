
给售卖NPC添加销售物品

方法一

选中一个 NPC，然后聊天栏输入命令：

```bash
.npc info
```

可以查到NPC的ID，例如是: 3053，然后：

select * from npc_vendor entry=3053

* entry: NPC ID;
* slot: 默认为 0。
* item: 物品ID；
* maxcount: 物品可出售的数量，0 表示数量不限。
* incrtime: 刷新时间，如果 maxcount 不为 0，则一定要填上刷新时间。
* ExtendedCost: 价格？默认为 0。

方法二

选中 NPC，然后在聊天框输入以下命令：

```bash
.additem itemid
```
