## Introduction

Smoke is very powerful. At the moment this is necessary, because it's
the only defense against maps with inescapable spawn positions. But it
is still too over-powered. A useful drawback would be to implement smoke
inhalation, whereby a soldier standing in smoke can eventually pass out
from lack of oxygen.

## Mechanism

Here is a simple mechanism to implement smoke inhalation. Each turn that
a soldier ends inside of a smoke field, he accrues a certain number of
SP (Smoke Points). When his SP exceeds his HP, he becomes unconscious.
SP will be displayed as a grey bar that covers the HP bar so players can
easily track it. Each turn that a soldier ends outside of a smoke field,
he loses a certain number of SP.

- SP gained per alien turn inside smoke: 40
- SP lost per alien turn outside smoke: 20

With these numbers, an average soldier with full HP (90-120) will pass
out after spending 3 alien turns inside smoke. A soldier who is wounded
will pass out the moment his SP exceeds his HP, whether that is during
an alien turn spent inside smoke or when he is injured.

## Resistance/Protection

Smoke could be a dmgtype and thus respond to resistance/protection
values. Organic units would have no resistance. Mechanical units would
have full resistance. In addition, armour should provide some protection
for this.

## Medikit

Raising a soldier's HP will be the obvious way to revive an unconscious
soldier in most cases. But if his SP exceeds his max HP, this will not
be sufficient. Should one of the medikit firemodes be capable of
reducing SP?

[Category:Proposals](Category:Proposals "wikilink")