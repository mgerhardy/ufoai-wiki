Is there a way to test if we have this "You need a 3D graphic card and a
suitable driver which is installed on your system"? In Linux that is...

-- xxx

How about `glxgears` or something similar? It should be installed on
most systems.

--[141.76.1.120](User:141.76.1.120 "wikilink") 12:15, 29 June 2006
(CEST)

    glxinfo | grep direct


should give *direct rendering: Yes*

[Mattn](User:Mattn "wikilink") 14:35, 29 June 2006 (CEST)

Here is the source code of howtoplay.html, in particular the keybidings
table. The pictures are not up to date (keybindings might be). And
mouse-over tooltips should do all the pictures did (don't they
already?). --[Bandobras](User:Bandobras "wikilink") 03:45, 14 July 2006
(CEST)

    <head>
        <link href="ufoai.css" rel="stylesheet" type="text/css"/>
    </head>

    <body>
        <h1>
            UFO: Alien Invasion Demo
        </h1>

        Welcome to the UFO: Alien Invasion demo. This document gives a short introduction on how the game is played. Please keep in mind that this is a technical demo only. A lot of things are not implemented yet or will be changed during development. Feel free to post questions and comments on the message board of our homepage: <a href="http://ufo.myexp.de" target="_blank">http://ufoai.net</a><br/>
        <br/>

        The game consists out of two main parts:<br/>
        - the <a href="#geoscape">geoscape</a><br/>
        - the <a href="#tactical">tactical missions</a><br/>
        <br/>

        Those of you, who already know the concept of this kind of game, may go directly to the controls.<br/>

        <h1>
            Starting a new game<br/>
        </h1>
        - Start the game<br/>
        - Click on Singleplayer<br/>
        - Click on New Game<br/>

        <h1><a name=geoscape></a>
            Geoscape
        </h1>
        Here you can do a lot of things in the finished game. In this demo version you can create a team, buy some weapons and start tactical missions.<br/>

        <br/>
        <img src="images/geoscape.jpg">
        <br/><br/>

        The first thing that has to be done is to create your squad. Click on <b>Equip</b>.<br/>
        Choose a total of 8 soldiers. You can start a mission with less than 8 soldier, but it�s not really recommended. After accomplishing missions, more soldiers will be available. If you don�t like the auto-generated names you can click on <b>EDIT</b> and give the soldier a different name. When you are done, click on the <b>continue</b>-button.<br/>

        <br/>
        <img src="images/team.jpg">

        <br/><br/>

        Your next task is to give some weapons to your squad. This can be done by drag-and-drop. Note that the weapons require different amount of space. Don�t forget to give your soldiers some additional ammo too. If you don�t know how the ammo for a certain gun looks like, you can click on the weapon and you see the ammo and a description of the gun on the lower left of your screen. You can also display the abilities of the soldier.<br/>

        <br/>
        <img src="images/weapon_equip.jpg">
        <br/><br/>

        The buttons Primary, Secondary, Misc and Ammo don�t work yet. The weapons will be sorted by category later. After giving all players weapons and ammo click on the <b>continue</b>-button. This will bring you back to geoscape. If you are running low on equipment, you can buy some by clicking on <b>Buy/Sell</b>. I think buying and selling things is quite self-explanatory, I won�t explain this here. You will get additional money if you successfully accomplish a mission. Important: You can save the game in the <b>Menu</b>. This might be a good idea, if you don�t want to equip the team each time you start a new game.<br/>
        <br/>

        OK, now you're ready to start a mission. Click on one of the red crosses on the world map. I recommend to start with the one at Fargo. After selecting it, a yellow circle appears around the cross. Click on the <b>Start Mission</b> button.<br/>

        <h1><a name=tactical></a>
            Tactical Missions
        </h1>

        First, here�s a list of the most important commands:<br/>
        <br>

        <table border="0" cellpadding="0" cellspacing="0" width="100%">
            <td width="10%">
                Mouse1(left):<br/>
                <br/>
                <br/>
                Mouse2(right):<br/>
                Mouse3(middle):<br/>

                'x':<br/>
                Mouse wheel:<br/>
                <br/>
                Left arrow:<br/>
                Right arrow:<br/>
                Up arrow:<br/>

                Down arrow:<br/>
            </td>
            <td width="50%">
                Select<br/>
                Press button<br/>
                Shoot (in fire mode)<br/>
                Walk<br/>

                Look in direction of cursor<br/>
                Look in direction of cursor<br/>
                Zoom<br/>
                <br/>
                Rotate view clockwise<br/>
                Rotate view counter-clockwise<br/>

                Up by one floor<br/>
                Down by one floor<br/>
            </td>
        </table>

        <br/>
        <img src="images/hud.jpg">
        <br/><br/>

        UFO:AI is a round based game. Each soldier has about 30 time units at the beginning of a round. By doing something like walking or shooting, time units will decrease. If a soldier has no time units left, there is nothing she/he can do in this round. When you are done giving you squad orders, you can end the round by clicking the <b>next round</b>-button. The aliens will move then. After that, your team members get new time units. <br/>
        This demo contains three terror-missions. This means, that you have to kill all aliens and protect civilians, if possible. The missions is won, if all aliens are eliminated.<br/>

        <h2>
            Walking, Selecting Floors, Rotate View
        </h2>
        Left-click a soldier to select him. Right click where you like him to move. To toggle between floors, use the arrow up and arrow down key. Floors can also be selected by the <b>Select-Floor</b>-buttons on the left of the screen. If you cannot see the area where you would like to walk, use the left and right arrow on your keyboard to rotate the view. To turn the soldier into a certain direction without moving, click on the middle mouse button.<br/>


        <h2>
            Shooting, Reloading
        </h2>
        If you see an alien, you can shoot at it, if you have enough time units left. Each weapon has a primary and a secondary fire mode. Normally, secondary fire is more powerful, but requires more time units. Click on <b>fire primary</b> or <b>fire secondary</b>. Your are in Fire-Mode now (cursor becomes a crosshair). In the info screen, you can see how many time units are needed to fire. Left-click on the alien to shoot at it. If you want to leave fire mode click the right mouse button. If the gun is empty click on <b>reload</b> button, or drag a new clip on the gun in the <b>inventory</b>.<br/>


        <h2>
            Crouch / Walk
        </h2>
        The <b>Crouch/Walk</b> button toggles between walking and crouching. A crouched soldier needs more time to move, but the accuracy of your weapon is higher.<br/>

        <h2>
            Inventory
        </h2>
        You can change, drop and take weapons in the inventory screen. Simply drag and drop.<br/>


        <h2>
            Ending a Round
        </h2>
        When you are done and most of the time units are used up click on the next round button on the upper right of the screen.<br/>

        <h1>
            That's it! Questions?
        </h1>
         Post them in our forum at <a href="http://ufo.myexp.de" target="_blank">http://ufo.myexp.de</a>.
    </body>

instead of generating html pages for howtos i would like to have a
sequence for the tutorials that are available in game. maybe someone
finds the time and generate a new sequence?


[Mattn](User:Mattn "wikilink") 09:35, 14 July 2006 (CEST)

I hope so. Anyway, keybiding table, as here on the wiki, is needed,
because nobody will run a tutorial just to recollect a particular
keybinding. BTW, what is the legal status of the old howtoplay.html
texts? They are quite to the point, so perhaps one could use them in the
in-game tutorials. --[Bandobras](User:Bandobras "wikilink") 17:21, 14
July 2006 (CEST)

## Parse errors?

I just compiled it, but I seem to be getting some kind of parse error
when I try to run it. I get lots of potential error messages like

    ...GL_ARB_fragment_program not found
    ...GL_ATI_separate_stencil not found
    ...max texture size:
    ......cannot detect !
    ...SDL_ttf version 2.0.8 - we need at least 2.0.7
    ...SDL_ttf inited
    ------------------------------------
    Can't find pics/wait
    CDAudio_Init: Unable to open default CD-ROM drive:
    ...using language: en_US
    ...svn revision:
    Com_ParseItem: unknown token "twohanded" ignored (weapon assault)
    Com_ParseItem: unknown token "true" ignored (weapon assault)

*many more like that*

    Com_ParseFire: unknown weapon skill "precise" ignored (weapon laserrifle_ammo)
    Shared Client/Server Info loaded
    Unknown command "loadteam"
    Unknown command "ov_start"
    ====== UFO Initialized ======

    SDL audio device shut down.
    recursive shutdown
    Error: ...could not find font: f_small

Seams like you are using data from another version - you can't mix 2.1
and 2.0 data (e.g)


[Mattn](User:Mattn "wikilink") 10:11, 21 February 2007 (CET)