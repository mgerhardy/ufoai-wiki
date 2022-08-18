## Description

The Squad Commander Campaign is a kind of mini-campaign in which the
player controls a single squad. After each mission, the squad's progress
is saved and the player will earn money that can be spent on improving
the squad's equipment. The player only controls the squad equipment,
soldiers and battlescape performance. There is no base management,
aircraft or any of the other aspects of the full campaign.

The Squad Commander Campaign will be designed as a multiplayer coop
campaign and can also be played in single player. Many of these same
features can also be used to play adverserial multiplayer games with a
persistent squad, but that could be a separate proposal once this system
is already in place.

## Story

The player is the commander of a mercenary company. He and his soldiers
are hired by countries and Phalanx to take care of specific mission
threats. This story would help explain why the player is able to turn
down missions.

## Squad Management

The player will begin the game with a squad of 32 recruits. If his
soldiers die, he will receive new recruits, but he will always have 32
recruits in his squad. From this squad, he must choose who will go on
certain missions depending on how many soldiers are supported (usually 8
to 12, I would guess). His goal is to retain his soldiers so that he
always has a strong team.

There should be a simple hospital system as well. It would be nice to be
able to dismiss soldiers, but since the player will always have 32
recruits, this could be used to dismiss soldiers over and over until you
get good recruits. There would need to be some way of preventing this --
perhaps a delay of one mission before new soldiers are available.

## Mission Progression

At any point during the game, the player should be able to choose from
easier or harder missions (3-5 mission), but the game will start with
easier missions. The player can look at what missions are available and
what the payment is for each mission. He can then choose the one he
would like. Missions are only available for a certain "period of time".
Most missions will be available only once (if the player chooses a
different mission, it will go away). But some special objectives
missions may be available for longer.

Harder missions of course bring more financial rewards. The player can
choose to do nothing but easy missions, but special objective missions
(see below) will always be harder and the player will be unable to
"advance" to new technology or advanced scenarios without beating these
more difficult missions.

The player should have control over the type and difficulty of the
missions he chooses to play, but successful completion of the game
should require him to tackle various missions. Disincentives could be
introduced for failing to handle important missions. Nations/Phalanx
could offer fewer missions or pay less money if they are unhappy with
the player's response. In the end, the player's contracts could be
suspended if they are unhappy with his performance.

## Economy/Equipment

The player will start with basic equipment and then he will be able to
purchase new equipment using credits he has earned from completing
missions. In some cases, new equipment will become available as the game
progresses, regardless of the player's actions (Phalanx has completed
research).

In other cases, the player will earn access to new equipment (that must
still be purchased) through the completion of successful missions. The
player can also pick up and use equipment retrieved during missions.

## Special Objectives

Special missions will appear from time to time. These may progress the
campaign in some way, or they could just have interesting objectives.
Possible missions: - Protect important facility/individual - Retrieve
item from a map (could advance technology) - Terror mission -
Investigate strange reports

## Hospital

Perhaps we will need some kind of hospital function to handle wounded
soldiers.

## Roadmap

This is a set of intermediate stages would could be implemented on the
way to full implementation of the proposal.

### Mark I

A simple system in which the player is given a new squad of 8 soldiers.
He must complete as many different missions as he can and after each
mission his progress is saved. He can always choose from the same
collection of weapons. There is no choice of missions. There is no
economy. When all of his soldiers die he loses. Victory is achieved when
he completes all missions.


Tasks


Support for saving the squad after each mission

Support for mapcycle

Setup of the new gametype in mp coop and skirmish

UI: Support for beginning the game in mp coop and skirmish

UI: Make sure the equip screen works for this gametype

### Mark II

Adds support for 32 soldiers in the squad and getting new recruits when
soldiers die. Game can not be "lost" but the player must still complete
all missions in order to win.


Tasks


New soldiers created when existing soldiers die

UI: Way to select which of the 32 soldiers to take on the next mission

### Mark III

Adds support for mission selection and special missions, and moves to a
generated campaign system (not just a map-cycle). After each mission,
the player can choose his next mission from several missions on offer.
Not all equipment is now available at the beginning of the game. Some
alien tech is opened up through special missions.


Tasks


Code must be written to generate a selection of missions (3-5) after
each mission balanced to offer easier and harder missions throughout the
game, and designed to progress through end-scenario missions

Code for special missions that grant access to alien tech when completed

UI: New interface for selecting the next mission and viewing each
mission's details

UI: Messages displayed when the player has access to new equipment

### Mark IV

Adds support for economy. Missions now bring in money and the player
must purchase weapons with that money. More special missions and
end-game


Tasks


Code must be written to track the player's credits and mission rewards

Mission definitions should include a price the offerer will pay for
successful completion

More special missions should be set up

UI: Equipment selection will now also need a market window

### Mark V

Adds support for the hospital and soldier dismissal


Tasks


Code to handle taking soldiers out of active rotation and putting them
in hospital

Code to dismiss a soldier

Code to delay new recruits to fill empty slots for one mission to
prevent abuse of dismissal

UI: Hospital view

UI: Dismiss soldier button

[Category:Proposals](Category:Proposals "wikilink")