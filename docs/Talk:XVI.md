## XVI Infection - Display on Geoscape (and elsewhere)

Ok, here some facts: We currently have some problems with displaying
overlaid "infection state" on the earth-image on the geoscape. This has
to to with multi-texture support and I do not know enough about that to
comment if (or when) this might be possible. Looking purely at the
technical side I would say it's just a matter of time until this works
as well, but that's me :)

Until this is cleared there are some other ways how we can display
infection state of each nation:

- The easiest way is of course displaying the infection-percentage as
  **text**
  - Place(s) is/are irrelevant for now, but suggestions are welcome
    (text next to nation-name on geoscape, in a nation-overview
    (funding), etc...)
  - This will be implemented no matter what else we add from the other.
- **Status bars** similar to the ones in the team-screen
  - Places are up for discussion
- **Custom images** for each 'state' *My personal favourite
  --[Hoehrer](User:Hoehrer "wikilink")*
  - e.g. A human face where the skin get's more and more XVI-like (See
    [TODO/XVI](TODO/XVI "wikilink") for more on that) the more infected
    the nation gets.
  - Placement is up for discussion.
  - Save thing could also be done for "Happiness" of the nation with
    PHALANX (but only with "smiling" -\> "raging" human face)

If I remember the discussion about the story-progress correctly the
display of XVI-spread will only be shown after a certain point in the
story. i.e. either after some research has been done or a similar event.
Any ideas on that?

--[Hoehrer](User:Hoehrer "wikilink") 14:25, 8 August 2007 (CEST)

- my idea: add new button to the geoscape buttons (near the "create new
  base" button), which will open "Nations" menu; such menu should
  contain several things, namely:
  - nation happiness: bars (current/max), an icon which will be
    graphical representation of happiness (and which could be used
    anywhere else), and "happiness name" as it is in our code
  - nation funding, which will point the montly fundings and new
    recruitements of the nation - maybe in the future we could this way
    block something, for example "we do not need more scientists, thank
    you"?
  - after certain campaign event, the XVI progress - which would be
    similar to the nation happiness

--[Zenerka](User:Zenerka "wikilink") 14:40, 8 August 2007 (CEST)

- Yes, such a "nations" screen is needed anyway, because there just
  isn't a good way to display all the nation-specific information
  directly in any existing screen. But some things just look better if
  they are visible directly on the geoscape (display most important
  information about a nation on mouse-over; either as a tooltip or in a
  field like the "mission description" field)
  --[Hoehrer](User:Hoehrer "wikilink") 15:03, 8 August 2007 (CEST)
  - I actually already started such a screen yesterday. It is only
    reachable by typing `mn_push nations` right now (WARNING: Do not try
    to use this and then save. The graph displays random values and
    messes up the happiness values for testing purpose!). So this will
    be another place to show infection-status once available.
    --[Hoehrer](User:Hoehrer "wikilink") 08:58, 10 August 2007 (CEST)

## XVI Infection - Display on Battlescape

"Display" not game-mechanics (such as soldiers getting infected):

- One thing I personally would like to see is civilians with
  unmistakable symptoms (or completed transformations) of XVI as
  described in [TODO/XVI](TODO/XVI "wikilink")
  ---[Hoehrer](User:Hoehrer "wikilink") 14:25, 8 August 2007 (CEST)
  - That's kind of tough. XVI does not really have external symptoms (a
    large part of the XVI research branch is centered around that
    principle), so it would be hard to make infected civilians easily
    recognizable. In fact, it might even be interesting to NOT
    distinguish infected civilians from "clean" civilians - imagine
    suddenly being attacked by the civilian you're trying to protect!
    - Good point and nice idea. Although I'm not sure about this part of
      the description then: <small>"*Eventually the skin will turn
      entirely pink-grey as XVI eliminates the remnants of the old
      immune system.*"</small> Is something not matching up here, or is
      this the phase _before_ XVI takes over compeltely? Also 'no
      external symptoms' really depends on the state of the infection we
      find the civilias in (first few minutes?)
      --[Hoehrer](User:Hoehrer "wikilink") 14:58, 8 August 2007 (CEST)
      - I had forgotten about that bit. We can use that. However, I
        should think that only applies to humans who have been infected
        by XVI for an appreciable amount of time (several days). Humans
        who have been recently infected should not appear differently
        from clean ones. Winter may want to give some input about this.
        --[BTAxis](User:BTAxis "wikilink") 15:13, 8 August 2007 (CEST)
        - This is where my "*first few minutes?*" comment from above
          comes in ... quote from the XVI page: <small>"*This results in
          a feeling of extreme illness for the victim, lasting anywhere
          between 30 seconds and 30 minutes, depending on the severity
          of infection. This period is marked by severe vomiting,
          erratic behaviour, and discolouration of the skin in the form
          of red and grey blotches.*"</small> An I would think PHALANX
          is fast enought to reach most sites in this time-frame?
          Anyway, yes I think Winter should have a look at this before
          we continue :). --[Hoehrer](User:Hoehrer "wikilink") 16:33, 8
          August 2007 (CEST)
          - Hm, you're right. Anyway, PHALANX can't get to most sites
            within 30 minutes - with the first dropship it takes hours
            to get anywhere and even with faster ships you can't cover
            everything with a response time of 30 minutes or less unless
            you built very many bases. Not to mention that the player
            may wait before dispatching the ships. I suppose that means
            that for all means and purposes, we can just give infected
            humans a different skin. --[BTAxis](User:BTAxis "wikilink")
            16:50, 8 August 2007 (CEST)

<!-- -->

- Something I would like to note also is that I'd prefer if XVI
  infection was not on a per-nation basis, but on a per-region basis,
  with every nation consisting of several regions. This is not really
  necessary for 2.2, but I feel it should be taken into consideration
  for later, more sophisticated versions.
  --[BTAxis](User:BTAxis "wikilink") 12:07, 4 September 2007 (CEST)

## Grammar

"virii" in not an English or Latin word. In English, "viruses" is the
proper plural, and there is no proper plural for it in Classic Latin. In
New Latin, "vira" is the (commonly unused) proper plural.