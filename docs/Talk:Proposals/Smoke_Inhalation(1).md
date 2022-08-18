- Would there be a resistance system, like the one for the gas grenades?
  The Power Armour is supposed to be airtight, so if a soldier wears one
  he cannot be affected. --[ShipIt](User:ShipIt "wikilink") 12:16, 21
  March 2013 (SAST)
  - Good point. --[H-hour](User:H-hour "wikilink") 16:27, 21 March 2013
    (SAST)
- How about a malus for skills/stats? Standing in smoke and the
  resulting lack of oxygen might lower the soldiers stats by using the
  proposed SP-system. So instead of falling unconscious he will have
  e.g. a lower accuracy until recovered?
  --[ShipIt](User:ShipIt "wikilink") 12:16, 21 March 2013 (SAST)
  - I don't know about this. Partly I feel like we're talking about such
    short bursts of time that a soldier ought to be able to be in smoke
    temporarily without any adverse effects. Partly I think that it
    would be very difficult to communicate this effect to players. On
    the other hand, I have thought about a basic accuracy penalty if a
    soldier has no line-of-sight to their target. But I've hesitated
    because I fear it will undermine smoke too much (and we still need
    it in badly). --[H-hour](User:H-hour "wikilink") 16:27, 21 March
    2013 (SAST)
    - Hehe, I was thinking the same about the accurace without a LoS.
      The skill malus was just an idea. I am fine with the proposed way.
      --[ShipIt](User:ShipIt "wikilink") 17:32, 21 March 2013 (SAST)

## Smoke Points (SP) and Stun Damage

DarkRain brought up some important points in a PM, so I'm copying them
here:

- If it is OK to (ab)use the stun damage, system it should be pretty
  easy, on the other hand, while implementing separate SP isn't that
  hard, it would be fairly more involved. (DarkRain)
  - I'd rather not use the stun damage if possible, simply because it is
    one of those solutions that will lend itself to a lot of questions
    about why the two things are linked. But I think it's fine if this
    doesn't make it into 2.5. It's not a necessary balancing mechanism.
    But since you bring up the stun damage, that will lead to some UI
    confusion too. Doesn't stun already cover the HP bar in grey?
    (H-Hour)
    - Yes, it does. And since we are discussing stun damage vs SP, what
      would be the relation between stun and SP damage, would they
      interact in any way? (DarkRain)
      - I don't know. To be honest I hadn't really thought that through.
        And I must confess when you said "stun" before I was confusing
        it with "shock". I will have to think about this some more.
        Maybe it's not such a bad thing for smoke to cause stun damage.
        We've already got stun_gas which is basically smoke that stuns.
        I guess the first major issue I can think of is that if a unit
        is stunned they should stay down for several turns, but my plan
        for the smoke was for it to be a pretty quick recovery once out
        of the smoke. But since we can't pick up soldiers and move them,
        maybe the smoke would accumulate and it would be several turns
        before a soldier recovered anyway. (H-Hour)
        - Well, since I read the proposal the first time I thought that
          SP was basically the same than stun damage, even if it is
          implemented separately (allowing smoke inhalation effects to
          fade faster), the fact that both stun and SP cause
          unconsciousness means they will have to interact somehow,
          maybe they could add together for checking when someone should
          fall unconscious or wake up?
          --[DarkRain](User:DarkRain "wikilink") 04:59, 29 March 2013
          (SAST)
          - From a designer's perspective I don't really like combining
            them all, because being electrocuted, being gassed and just
            being in smoke are all very different things in "real life".
            But on further thought I just don't think this justifies
            adding a new mechanic for players to track. All three can
            simply provide stun damage and we'll leave it at that. But
            it raises another issue, which is that stun gas and
            electrocution stunning ought to be much more effective than
            regular smoke, or we will render these tools obsolete. I'll
            have to look into the balance for the stun_\* weapons, but
            my first thought is that they should generally, reliably
            incapacitate a unit in one hit, to make them valuable enough
            to field in addition to smoke grenades. Do they accumulate
            stun damage just like other weapons (ie - damage value is
            applied the same)? And how does recovery work for stunned
            units? --[H-hour](User:H-hour "wikilink") 15:12, 29 March
            2013 (SAST)
            - From the technical point of view it should be no problem
              to given the smoke field a trigger that triggers stun
              damage. We should just define how much.
              --[Mattn](User:Mattn "wikilink") 15:16, 29 March 2013
              (SAST)

## Realism

Current lore depicts smoke grenade as being based on the titanium
tetrachloride. This substance indeed creates thick smoke when dispersed
in air, by reacting with water vapor and producing titanium oxide(IV),
which creates the smoke, and hydrochloric acid fog which is responsible
for both the additional "smoke", and the toxic effects of the cloud.

So, realistically, smoke grenade should cause both stun and health
damage for those standing in the cloud -- unless said ones have some
protective clothes, or, at least, a gas mask.

Google for "hydrochloric acid poisoning", if you want to know about
actual effects.