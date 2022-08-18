\[mail_stunned_alien_died\]
先生，在%s基地关押的异形俘虏突然死了。我们还不知道为什么会这样。

\[*Arguments:*\] base name

---

\[mail_alien_ufo_crashed\]
先生，%s损坏太严重。我们只找到了部分可用的部件。以下是运回%s的部件清单：

%s

\[*Arguments:*\] ufo name -- base name -- list of item that could be
collected aboard this ufo.

---

\[mail_alien_ufo_recovered\]
先生，我们在这里找到了%s，正在组织工程师分解，我过几天才能%s。

以下是我们分解收获的清单：

%s

\[*Arguments:*\] ufo name -- base name -- list of item that could be
collected aboard this ufo.

--- \[mail_aircraft_landed\]
指挥官，%s已经在%s着落，正在%s，预计需要%s小时。

-- 航管塔

\[*Arguments:*\] aircraft name -- base name -- current status
{refuelled/refuelled and rearmed/repaired, refuelled and rearmed} --
time before craft is ready for launch.

\[mail_aircraft_bingo_fuel\] 指挥官，%s
没燃料了。他只好返回%s。任务放弃。

-- 航管塔

\[*Arguments:*\] aircraft name -- base name.

\[mail_aircraft_ready\] 指挥官，%s已经%s，随时待命。

-- 航管塔

\[*Arguments:*\] aircraft name -- current status {refuelled/refuelled
and rearmed/repaired, refuelled and rearmed}.

\[mail_aircraft_lost_target\]
指挥官，%s追踪%s雷达失去目标。请提供下一步命令。

-- 航管塔

\[*Arguments:*\] aircraft name -- pilot status {The pilot has managed to
eject safely and is currently being recovered/The pilot failed to eject
in time} -- dropship troop status -- {The dropship's troop compartment
was saved and X of our agents will be returned to base.}

\[mail_aircraft_new_at_base\]
指挥官，%s已经抵达%s，检测正常，随时可以使用。

-- 航管塔

\[*Arguments:*\] aircraft name -- base name.

\[mail_alien_activity_reported\] 早上好，先生。

我们发现在%s有外星人活动，那里很恐慌。我建议马上派队伍过去。祝你好运。

法兰克上校

\[*Arguments:*\] mission location.

\[mail_alien_base_discovered\]
先生，我们的特工在%s发现有个巨大的外星人基地。这个在地球上的基地对PHALANX对人类都是个巨大的威胁，我们必须马上行动。

\[*Arguments:*\] nation name.

\[mail_mission_summary\] 先生，我这里有一份%s现阶段的简报。

任务%s。%s%s了，他们与我们的关系变得%s。

任务中共消灭了%s异形。%s士兵在任务中阵亡，%s市民死亡。

清理战场收获了%s物资，俘获了%s敌人和%s尸体。

%s

\[*Arguments:*\] location name -- mission result-dependent string
{success/failure} -- nation name -- mission result-dependent string
{impressed/disappointed} -- mission result-dependent string
{improved/deteriorated} -- number of aliens killed in mission -- number
of PHALANX troops killed in mission -- number of civilians killed in
mission --number of items recovered -- number of live aliens recovered
-- number of alien corpses recovered -- UFO handling-dependent string
{The UFO has been recovered and transferred to a UFO hangar/The UFO was
recovered but had to be discarded for lack of space.}.

\[mail_base_attack_report\] 这里是敌人攻击我们%s的报告。

任务%s发生在%s。

%s设施受到轻微损害。

%s

%s设施受到严重损害，需要立即修复，修复费已从预算中扣除。

%s

%s设施被完全摧毁。

%s

在战斗中共消灭了%s异形，我们损失了%s士兵。

清理战场收获了%s物资，俘获了%s敌人和%s尸体。

%s

\[*Arguments:*\] base name -- mission result-dependent string
{success/failure} -- nation name -- mission result-dependent string
{held/lost} -- number of minor damaged facilities -- list of minor
damaged facilities -- number of major damaged facilities -- list of
major damaged facilities -- number of destroyed facilities -- list of
destroyed facilities -- number of aliens killed in mission -- number of
PHALANX troops killed in mission -- number of items recovered -- number
of live aliens recovered -- number of alien corpses recovered -- UFO
handling-dependent string {The UFO has been recovered and transferred to
a UFO hangar/The UFO was recovered but had to be discarded for lack of
space.}.

\[mail_new_base\] 新基地的基本物资和场地已准备好了。%s现在可以建设了。

\[*Arguments:*\] base name.

\[mail_construction_finished\]
新的%s已建造完毕，%s可以开始使用这个设施。

\[*Arguments:*\] facility name -- base name.

\[mail_transfer_received\] 向%s运输的任务已完成。

\[*Arguments:*\] base name.

\[mail_ufo_in_hangar\]
指挥官，俘获的%s已回收到%s，现在我们可以开始分解它了。

--Cdr. Navarre

\[*Arguments:*\] UFO name -- base name.

\[mail_monthly_report\] 先生，月底结算的时候到了。这里是总结报告。

维护

基地维护：%s c

飞机维护：%s c

装备消耗：%s c

合计花费：%s c

施工

基地建设：%s c

设施建设：%s c

合计花费：%s c

薪金

士兵： %s c

工人： %s c

研究员：%s c

飞行员：%s c

合计花费：%s c

制造

成本： %s c

贸易

购买飞行物： %s c

出售飞行物： %s c

购买装备： %s c

出售装备： %s c

合计： {+/-} %s c

国际组织

联合国整体觉得{happy/satisfied/unhappy}，比上个月{increased/maintained/decreased}。

资助额{next month}: %s c

上个月资助额： %s c

变化： {+/-} %s c

预算合计

总收入： %s c

总支出： %s c

库存： %s c

月报统计

异形活动： %s

总任务数： %s

任务成功： %s

任务失败： %s

发现UFO： %s

击落UFO： %s

消灭敌人： %s

俘获敌人： %s

士兵损失： %s

飞机损失： %s

新建基地： %s

摧毁基地： %s

\[mail_production_finished\]
{location}已完成{item}的制造，经测试符合使用要求。

--Cdr. Navarre

\[*Arguments:*\] lots.

\[mail_prolog\]
欢迎您，长官。现在，PHALANX外星反应部队全部由您指挥。你的任务是要保护地球上的人类并不惜一切代价阻止外星侵略。如何做到这一点就看您的了。我们唯一的要求就是必须成功。

您的第一个任务是建立一个总部。联合国已经批准可以在世界各地任何地方建设军事基地，您只需要仔细考虑把基地建在何处。选择的位置很重要，这将直接影响PHALANX是否可以成功。

最近一项对孟买和波恩所受袭击的分析显示，UFO似乎集中在人口稠密地区活动，包括南北美洲，欧洲，东亚，南亚，地中海，非洲和澳大利亚的沿海地区。你应该考虑在这些地方建立你的基地。

一旦你建立好你的第一个基地，你就要装备好你的士兵。这些PHALANX的新兵应该分配到登陆机上，随时准备战斗。

照顾好他们，长官。我们全都指望你了，为你祈祷。

祝您好运。

[Category:Contribute](Category:Contribute "wikilink")
[Category:Translating](Category:Translating "wikilink")