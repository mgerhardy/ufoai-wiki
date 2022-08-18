**ДО:** Base Commander, PHALANX, Atlantic Operations Command

**ОТ:** Dr. Connor, R&D: Bio & Containment Division, PHALANX, Atlantic
Operations Command

**ДАТА:** %02i %s %i

**ОТНОСНО:** Urgent -- Alien Specimen Failure

Commander,

I'm afraid I have some bad news. Despite our best efforts, the alien
specimens recovered from our last tactical mission have expired in
Containment. We were ultimately unable to stabilise their medical
condition enough to learn anything useful.

Outward signals indicate the cause of death to be sudden and fatal
asphyxiation. It seems the aliens can only live in our atmosphere for a
limited time before they suffocate. We haven't performed a full
examination on the body, not without your authorisation, but I strongly
recommend that we move straight to autopsy at this point. We must find a
way to keep them alive longer or we won't be able to conduct any
meaningful research on them.

My autopsy request should be waiting in the R&D queue for your approval.
Thank you, Commander.

Sincerely, Dr. Connor

*`Prerequisites:`*
` The first live alien has died in containment because Alien Breathing Apparatus has not been`
` researched, AND Alien Breathing Apparatus is not available for research.`

**The contents of this page are not yet ready for translation because
the source material is likely to change.**

This notice will be removed when the page is ready.

\[mail_stunned_alien_died\] Sir, the stunned aliens we captured during
the battle all died in base %s. We currently have no idea why that has
happened.

\[*Arguments:*\] base name

---

\[mail_alien_ufo_crashed\] Сър, %s е прекалено повреден за да бъде
извлечен. Въпреки това успяхме да спасим част от апаратурата от
останките. Следното оборудване ще пристигне в %s със нашия транспортен
кораб:

%s

\[*Arguments:*\] ufo name -- base name -- list of item that could be
collected aboard this ufo.

---

\[mail_alien_ufo_recovered\] Сър, нашия отряд обезопаси %s на бойното
поле. Организирал съм да бъде ескотриран до %s до два дни.

При пристигането ще го разглобим за части. Нашите инженери описват
следната екипировка като използваема:

%s

\[*Arguments:*\] ufo name -- base name -- list of item that could be
collected aboard this ufo.

---

\[mail_aircraft_landed\] Командире, %s кацна в %s. Сега се %s.
Очакваното време време за обслужване преди готовност за полет е %s часа.

-- COMAIR

\[*Arguments:*\] aircraft name -- base name -- current status
{refuelled/refuelled and rearmed/repaired, refuelled and rearmed} --
time before craft is ready for launch.

\[mail_aircraft_bingo_fuel\] Командире, %s е просрочил летателното
време. Има гориво само за да се върне в %s. Мисията се отменя.

-- COMAIR

\[*Arguments:*\] aircraft name -- base name.

\[mail_aircraft_ready\] Командире, %s е бил %s и е готов за действие.

-- COMAIR

\[*Arguments:*\] aircraft name -- current status {refuelled/refuelled
and rearmed/repaired, refuelled and rearmed}.

\[mail_aircraft_lost_target\] Командире, %s изгуби радарното
проследяване на %s и не може да го поднови. Очаквам нови заповеди.

-- COMAIR

\[*Arguments:*\] aircraft name -- pilot status {The pilot has managed to
eject safely and is currently being recovered/The pilot failed to eject
in time} -- dropship troop status -- {The dropship's troop compartment
was saved and X of our agents will be returned to base.}

\[mail_aircraft_destroyed\] Commander, {aircraft} has been shot down by
hostile action. %s.

%s

-- COMAIR

\[*Arguments:*\] aircraft name -- target name.

\[mail_aircraft_new_at_base\] Commander, %s has arrived at %s and has
cleared its diagnostics and pre-flight tests. It is ready to launch at
your say-so.

-- COMAIR

\[*Arguments:*\] aircraft name -- base name.

\[mail_alien_activity_reported\] Добро утро, Сър.

Имаме потвърждение за живи извънземни в %s. Цивилните са изложени на
риск; Препоръчвам незабавно да се изпратят войници в района. Късмет и
добър улов.

С най-добри пожелания,

полк. Falkland

\[*Arguments:*\] mission location.

\[mail_alien_ufo_downed\] Good morning, Sir.

We've shot down an alien craft. The UFO has crash-landed in the national
territory of {nation}, and I've already secured permission for our
troops to go in and recover the craft. We should dispatch a dropship
immediately.

With kind regards,

Col. Falkland

\[*Arguments:*\] nation of crash site.

\[mail_alien_response_too_late\] Good morning, Sir.

I thought I'd let you know, the enemy force at %s seems to have
successfully %s due to our failure to respond. All hostiles have
disappeared %s. %s civilians died in the incident, and our reputation
has suffered as a result.

With kind regards,

Col. Falkland

\[*Arguments:*\] location name -- mission type-dependent string
{completed its mission/repaired its UFO} -- mission type-dependent
string {into the countryside/into orbit} -- number of civilians killed.

\[mail_alien_new_radar_contact\] Sir, radar is tracking an unidentified
target on our screens. %s has no scheduled flight plan and is not
responding to hails. We should launch an interception immediately.

\[*Arguments:*\] target name.

\[mail_alien_lost_radar_contact\] Sir, the unidentified object %s has
disappeared from our radar screens. All attempts to reacquire %s have
failed and we have no further knowledge of its whereabouts and
activities.

\[*Arguments:*\] target name -- target name.

\[mail_alien_base_discovered\] Сър, нашите агенти са открили
местоположението на голямо извънземно съоръжение на Земята на територия,
принадлежаща на %s. Това съоръжение представлява сериозна заплаха за
PHALANX и за човечеството като цяло. Трябва да го отстраним колкото може
по-скоро.

\[*Arguments:*\] nation name.

\[mail_mission_summary\] Sir, I have a brief report for you of our
mission to %s.

The mission was a %s. The hosting country, %s, was %s with our
performance and our relations with them have %s.

%s aliens were found and killed by PHALANX troops. %s PHALANX troops
were killed or are missing in action, and %s civilians were killed over
the course of the mission.

%s items have been recovered from the battlefield and moved to base
storage. We captured %s live enemy specimens and retrieved %s bodies.

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

\[mail_base_attack_report\] Here is the report regarding the alien
attack on our installation %s.

The mission was a %s. We %s the base.

%s facilities received minor damage and are being repaired at no
significant cost.

%s

%s facilities received major damage, requiring immediate repair.
Refurbishment costs have been subtracted from our budget.

%s

%s facilities were completely destroyed in the attack.

%s

%s aliens were killed during the fighting. %s PHALANX troops were killed
or are missing in action.

%s items have been recovered from the battlefield and moved to base
storage. We captured %s live enemy specimens and retrieved %s bodies.

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

\[mail_new_base\] Ownership of our new base has been transferred and the
premises have been secured. %s is now ready for construction.

\[*Arguments:*\] base name.

\[mail_construction_finished\] A new %s has been completed and is now
operational in %s.

\[*Arguments:*\] facility name -- base name.

\[mail_equipment_received\] The new equipment we ordered has arrived at
%s. It's been tested and is ready for use.

\[*Arguments:*\] base name.

\[mail_transfer_received\] The transfers you ordered for %s have arrived
and are ready to go.

\[*Arguments:*\] base name.

\[mail_ufo_in_hangar\] The recovered %s has arrived at one of our UFO
Hangars in %s, Commander. We can now start disassembling it for parts.

--Cdr. Navarre

\[*Arguments:*\] UFO name -- base name.

\[mail_monthly_report\] Sir, our monthly budget and performance review
is due today. Here are the figures and overview of our operations.

MAINTENANCE

Base maintenance: %s Credits

Aircraft maint.: %s Credits

Equipment maint.: %s Credits

Total maintenance: %s Credits

CONSTRUCTION

Base construction: %s Credits

Facility construction: %s Credits

Total construction: %s Credits

SALARY

Soldiers salary: %s Credits

Workers salary: %s Credits

Scientists salary: %s Credits

Pilots salary: %s Credits

Total salary: %s Credits

PRODUCTION

Production costs: %s Credits

TRADE

Aircraft bought: %s Credits

Aircraft sold: %s Credits

Equipment bought: %s Credits

Equipment sold: %s Credits

Total bought/sold: {+/-} %s Credits

UNITED NATIONS

The UN has been {happy/satisfied/unhappy} with our overall performance
and has {increased/maintained/decreased} its funding for the PHALANX
project this month.

UN funding for {next month}: %s Credits

Funding for previous month: %s Credits

Change: {+/-} %s Credits

BUDGET TOTAL

Total income: %s Credits

Total expenditures: %s Credits

Current funds: %s Credits

MONTHLY STATISTICS

Alien activity reports: %s

Missions performed: %s

Missions succeeded: %s

Missions failed: %s

UFOs spotted: %s

UFOs shot down: %s

Enemies killed: %s

Enemies captured: %s

Soldiers lost: %s

Aircraft lost: %s

Bases built: %s

Bases lost: %s

\[mail_production_finished\] Инженерния екип завърши производството на
{item} в {location}. Всичката екипировка е тествана и е готова за
употреба.

--ком. Navarre

\[*Arguments:*\] lots.

\[mail_production_not_enough_resources\] There aren't enough materials
to continue production of %s at %s. The production has been suspended.

--Cdr. Navarre

\[*Arguments:*\] item name -- base name.

\[mail_production_not_enough_money\] We're too low on funds to continue
production of %s at %s. The production has been suspended.

--Cdr. Navarre

\[*Arguments:*\] item name -- base name.

\[mail_prolog\] Welcome to your new post, Commander. You now have full
command over the PHALANX Extraterrestrial Response Unit. Your mission is
to protect the citizens of Earth and stop the alien threat at all costs.
How you accomplish this is up to you; our only requirement is that you
succeed.

Your first order of business is to set up a headquarters. The UN has
access to military bases all over the world, so you may consider any
region for your base of operations. Choose the location wisely, because
it will have great influence on the success of the PHALANX project.

A recent analysis of the attacks on Mumbai and Bonn reveal that UFO
sightings and alien activity seems to focus on the most densely
populated regions of Earth, including coastal North- and South-America,
Europe, Eastasia, South and Mediterranean Africa, and Australia. You
should consider including these territories in your field of operations.

Once you've established your first base, you must prepare your soldiers.
The recruits we have assigned to PHALANX must be stationed on your
dropship, then equipped for battle.

Take care of them, Commander. The rest of us are all counting on you,
and praying for you.

That is all. Good luck and good hunting.

\[mail_prolog_2\] Commander, this is just to let you know that the XO
and I have logged all our findings from the UN-requested Excalibur
Program to the system. They should now be available for you to read on
the UFOpaedia database, all articles are flagged with security
classifications based on who might find the information useful. Only you
and the XO have Sigma-level clearance -- these documents may warrant
special attention.

Since you were only just brought in, here is a quick introduction to the
Excalibur Program, just in case the UN haven't fully briefed you.

---

The alien attack on Mumbai made our situation painfully clear. Their
technology is far more advanced than ours. The complete inability of
Commonwealth troops to make a dent in the Mumbai offensive revealed
critical weaknesses in current military training and equipment. They
lost three battalions just bringing the aliens to a standstill without
inflicting significant casualties. PHALANX has to overcome these odds,
and to do that we need the very best human technology has to offer.

The Excalibur Program was created to find the most effective weapons on
Earth by reviewing their manufacturing standards, durability,
operational record, and their combat performance in the situations where
we've managed to bring the aliens to battle. These are weapons that we
consider to be the pinnacle of their class, and we can allow nothing but
the best to be in our agents' hands when we engage the aliens.

Also, from our experiences in Mumbai and other stricken cities, we've
concluded that the aliens seem to concentrate their efforts on
population centres, especially dense urban areas. A majority of
engagements have taken place at pistol or even knife-fighting range. For
the purposes of the Program, we've chosen several high-performance
weapons for our Close Range Combat package and given them designations
beginning with CRC.

The third part of our mission was to find armour and other items of
battlefield utility to help our soldiers complete their missions and
return to base alive. These items are all designed to increase a
soldier's combat effectiveness or general survivability.

Lastly, we needed to select aircraft capable of intercepting the
attacking UFOs and outfit them with armaments and equipment that will
give them a fighting chance against these alien craft. We have evaluated
every available piece of kit on Earth as part of the Program and we have
selected the very best for the defence of our planet.

All my files should be ready to review at your convenience, Commander.

--Cdr. Navarre

[Category:Contribute](Category:Contribute "wikilink")
[Category:Translating](Category:Translating "wikilink")