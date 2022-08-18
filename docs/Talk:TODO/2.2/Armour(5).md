- "Damage reduction values and scripts" -\> `dmgweight xxxxx`
  - Very nice concept - a lot better than the "every single ammo has a
    defined reduction value" and very easy to look at and tweak. :)
    --[Hoehrer](User:Hoehrer "wikilink") 16:00, 7 August 2007 (CEST)
- I also have no objections to this proposal and I also like it very
  much. So, if there is nothing more to discuss or no further
  objections, I would propose to consider it final and prepare TODO
  section for it (2.2, I believe we should have working armours in 2.2
  this way or another, and while this proposal is
  nice...)--[Zenerka](User:Zenerka "wikilink") 20:20, 7 August 2007
  (CEST)

## Armour, cont'd

I'd like to propose some armour-related functionality in addition to the
behavior described in the main article. Aside from a damage modifier, I
propose armour to also have a TU modifier. This modifier is subtracted
from a soldier's TUs at the beginning of his/her turn, meaning wearing
the armour effectively results in a reduction of max TUs for that
soldier. Light armours will have a TU penalty of zero, while heavier
armours will encumber the soldiers that wear them. One way to go about
it is by making the TU penalty a fixed value, defined in the script
files. However, it may be a good idea to scale the encumbrance based on
a soldier's strength stat. This could be a formula, but I believe it
would be better to define three or five penalty values that apply to a
certain range of the strength stat. For example:

    item medium
    {
        ...
        encumbrance
        {
            worst   20
            bad     17
            average 14
            good    11
            best    8
        }
    }

This would mean that a soldier with a strength rating below 20% will be
slowed down by the medium arour for 20 TUs while a soldier with a
strengh rating of 80% or higher will only be slowed down for 8 TUs.\*

The net effect of such a system will be that the player will have to
make a tradeoff between 1) effectiveness versus one damage type as
opposed to effectiveness against another and 2) overall effectiveness,
TU penalty and soldier strength. I believe that this adds depth to the
game while still being sufficiently simple for the player to grasp.

<FONT SIZE=1>\* This touches the subject of supposedly-elite soldiers
being "awful" at any given attribute. This is a separate discussion, but
I for one consider it valid.</FONT>
--[BTAxis](User:BTAxis "wikilink") 18:32, 8 August 2007 (CEST)

- while this new proposition (about TU reducing effect) is very nice and
  I am all for it, the proposed algorithm would require large amount of
  new code (at the first look); wouldn't be enough (read: enough, does
  not mean: better) to just add one static value to (almost) every
  armour (for example: reduce 15) and prepare the code, where we can use
  character strenght to determine how many of such (reduce 15) value
  should be removed at the beginning of character turn? (so, if strenght
  is worst, take 100%, if strenght is best, take 20%, and so
  on)--[Zenerka](User:Zenerka "wikilink") 20:55, 10 August 2007 (CEST)

what is wrong about the code we are using right now in **G_Damage**?

        /* Apply armor effects. */
        if (damage > 0 && ent->i.c[gi.csi->idArmor]) {
            objDef_t *ad;
            int totalDamage;

            ad = &gi.csi->ods[ent->i.c[gi.csi->idArmor]->item.t];

            totalDamage = damage;

            if (ad->protection[fd->dmgtype] > 0)
                damage *= 1.0 - ad->protection[fd->dmgtype] * ent->AP * 0.0001;
            else
                damage *= 1.0 - ad->protection[fd->dmgtype] * 0.01;

            if (!mock) {
                if (ad->hardness[fd->dmgtype]) {
                    int armorDamage;

                    armorDamage = (totalDamage - damage) / ad->hardness[fd->dmgtype];
                    ent->AP = max(0, ent->AP - armorDamage);
                }
            }
        }

## our damage types are the following:

    damagetypes standard
    {
        "_normal"
        "_steelblade"
        "_monomolecularblade"
        "_blast"
        "_fire"
        "_shock"
        "_laser"
        "_plasma"
        "_particlebeam"
        "_stun"
    }


[Mattn](User:Mattn "wikilink") 19:34, 4 October 2007 (CEST)

- Firstly, we're going to have more "damage types" than these, as stated
  in the article. Secondly, hardness shouldn't be used anymore.
  Thisrdly, the current code modifies damage by a multiplier while it
  should be a subtraction.


In addition, we need functionality for the new script entries as well as
a display somewhere in the equip menu for the judged armour values.
--[BTAxis](User:BTAxis "wikilink") 01:28, 5 October 2007 (CEST)