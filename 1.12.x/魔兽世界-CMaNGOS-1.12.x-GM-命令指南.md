# 魔兽世界 CMaNGOS 1.12.x GM 命令指南

标签： WoW 魔兽世界 CMaNGOS 1.12.1

---

## 1. 账号管理

**注：以下所有命令，需在游戏中的聊天框中输入，并回车运行，下同。**

### 在线创建账号

```bash
格式：
.account create $account $password

例如：
.account create test test123
```

注：该命令需要 `GM (4级)` 权限。

### 在线修改密码

```bash
格式：
.account set password $account $password $password

例如：
.account set password test test123 test123
```

注：该命令需要 `GM (4级)` 权限，可以修改任意玩家的密码。

### 在线修改自己的密码

```bash
格式：
.account password $old_password $new_password $new_password

例如：
旧密码是 12345，想修改密码为 abcde，命令为：
.account password 12345 abcde abcde

新密码需要输两遍，以便确认无误。
```

注：该命令只能修改自己的密码，且不需要 `GM` 权限，即普通玩家权限也可以自行修改自己的密码。


## 2. 常用命令

### 提升人物等级

```bash
.levelup 59             # 为当前目标(或自己) 提升 59 级, 满级 60 级
```

### 获取金币

```bash
.modify money 99999999  # 为当前目标(或自己) 增加 9999 金 99 银 99 铜
```

### 学习职业技能

```bash
.learn all_myspells     # 为当前目标(或自己) 学习当前职业所有的技能(不包含天赋点出来的技能)
```

注：学完技能后需要自己手动点天赋，或者找职业训练师重置天赋。点完天赋后，再去训练师处学习天赋点出来的技能，跟怀旧服一样。

### 学习武器熟练度

```bash
.maxskill               # 将已学会的武器技能学至300/300 (单手剑\双手剑\熟练度...等)
```

注：每个职业默认还没学会的武器技能，需要先去各主城的武器大师 `NPC` 处学习，学完以后，可以再次执行该命令。

### 学习专业技能

把某个专业技能的技能点数学到满级（300点），且学习所有可能的配方或图纸。

```bash
.learn all_recipes 工程学
.learn all_recipes 附魔
.learn all_recipes 裁缝
.learn all_recipes 炼金术
.learn all_recipes 锻造

英文版：
.learn all_recipes engineering
.learn all_recipes enchanting
.learn all_recipes tailoring
.learn all_recipes alchemy
.learn all_recipes smithing
```

注：可以学习超过 `2` 个专业技能，除特殊情况，一般建议学 `2-3` 个专业技能即可。

### 学习生活技能

把某个生活技能的技能点数学到满级（300点），且学习所有可能的配方或图纸。

```bash
.learn all_recipes 急救
.learn all_recipes 烹饪
.learn all_recipes 钓鱼

英文版：
.learn all_recipes firstaid
.learn all_recipes cooking
.learn all_recipes fishing
```

### 获取背包

```bash
背包 ItemID：

17966   奥妮克希亚皮袋
14156   无底包
19914   豹皮背包（唯一）

.additem 17966          # 为当前目标(或自己) 增加一个奥妮克希亚皮袋
.additem 14156          # 为当前目标(或自己) 增加一个无底包
.additem 19914          # 为当前目标(或自己) 增加一个豹皮背包（唯一）
```

注：更多的背包 `ItemID` 请参阅后面章节中更详细的背包列表。

### 获取坐骑

```bash
坐骑 ItemID：

19902   迅捷祖利安猛虎
19872   拉扎什迅猛龙
13335   死亡军马的缰绳 (DK马)

.additem 19902          # 为当前目标(或自己) 增加一个 迅捷祖利安猛虎 坐骑
.additem 19872          # 为当前目标(或自己) 增加一个 拉扎什迅猛龙 坐骑
.additem 13335          # 为当前目标(或自己) 增加一个 死亡军马的缰绳(DK马) 坐骑
```

注：更多的坐骑 `ItemID` 请参阅后面章节中更详细的坐骑列表。

## 2. 其他命令


**不太推荐使用的命令**

还有更强大的命令，因为过于 `imba`，和怀旧服差别太大，所以不推荐使用，例如：

```bash
.learn all_myclass      # 为当前目标(或自己) 学习当前职业的全部技能（包括天赋点出来的技能），且天赋点数全开（可超过51点）
.learn all_mytalents    # 为当前目标(或自己) 学习所有天赋点出来的技能，且天赋点全开（可超过51点）
```

