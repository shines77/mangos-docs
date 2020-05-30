# CMaNGOS mangosd 数据库表名

```bash
account 帐号
areatrigger_involvedrelation 传送（区域触发）包含的关系，可能
areatrigger_tavern 进传送门id指向template----OK触发
areatrigger_template 传送区域的具体坐标等(与travern所对应)
auctionhouse 拍卖行（参数--观看时所对应）
auctionhouse_bid 拍卖行的投标
auctionhouse_item 不明
bugreport 应该是给GM发信所对应的数据
character 创建的人物资料对应playercreateinfo
character_action 创建的人物所会的技能对应playercreateinfo_action（仅出生）
character_aura 不明
character_homebind 创建人物的出生地
character_inventory 创建人物的包里的东西
character_kill 创建人物的荣誉信息(杀或被杀，有无荣誉等）
character_pet 创建人物的宠物信息
character_queststatus 创建人物的任务信息
character_reputation 可能是声望（不明）
character_social 好友列表
character_spell 人物的魔法书（仅会魔法的人才会出现ID）
character_ticket 不明
character_tutorial 不明
command  GM 命令
creature NPC 怪物等信息
creature_grid 可能是跟NPC对话的有效距离（不明）
creature_involvedrelation NPC或怪物（特殊类）可给与任务（不明）
creature_movement 怪物或NPC移动的关系，活动范围
creature_questrelation 不明
creature_template 怪物或NPC的具体信息如HP，SP等
game_corpse 尸体所在地信息
game_graveyard 人物死亡后所回到的墓地（复活需要对应game_corpse表）
game_spell 魔法（参数有可以创造什么，比如FS做水）
game_talent 的天赋系统
game_weather 天气系统
gameobject 物品信息（地上的箱子，草，矿）仅刷新点，时间，位置
gameobject_grid 可以拿取的有效距离（不明）
gameobject_template 具体物品信息所对应的 草，矿等
guild 工会信息
guild_member 工会成员
guild_rank 工会的阶级系统
ip_banned 被封的IP列表
item_instance 不明
item_page 中任务的内容(不明）
item_template 道具及任务物品的详细信息
loot_template 掉率
mail 邮件系统
mail_item 邮物品的信息
npc_gossip NPC没事说的话，比如暴风城的小孩，BOSS遇到你说的话
npc_gossip_textid 话的内容对应NPC_gossip
npc_option 不明
npc_text 跟NPC说话的内容，不同于任务内容
npc_trainer 训练师所对应的内容
npc_vendor 卖东西的NPC
object_involvedrelation 物品之间的关系（交还任务吧，不明）
object_questrelation 不明（估计这2个之间应该有个是物品合成）
playercreateinfo 人物出生的信息，character是根据此系列来的，就不解释了
quest_template 任务的详细信息（可接范围等）对应QUESTID可能跟object_involvedrelation有关系
realmlist 服务器的登入信息（IP等）
taxi_node WOW的飞机系统（具体不明）
taxi_path 飞到哪的价格什么的吧（不明）
taxi_pathnode 飞机的完整表（对应taxi_NODE taxi_path）
```
