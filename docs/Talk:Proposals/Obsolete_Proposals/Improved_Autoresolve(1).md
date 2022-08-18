Some points of note:

- In theory, missions can be lost even though all aliens died, and
  conversely missions can be won even though all PHALANX soldiers died.
- The balance of power calculation might be biased in favor of the
  aliens too much.
- Possibly only the equipment scores for equipment in the hands should
  be counted to prevent abuse by overloading soldiers with useless
  equipment.

--[BTAxis](User:BTAxis "wikilink") 10:58, 4 September 2008 (UTC)

`int i;`
`float soldierSum = 0.0f;`
`float numbers, balanceOfPowerIndex;`

`/* wounded soldiers only count like healed ones - so teamSize `
` * will maybe differ some soldierSum */`
`for (i = 0; i < aircraft->teamSize) {`
`  const character_t *chr = &aircraft->acTeam[p]->chr;`
`  const float factor = (float)chr.HP / (float)chr.maxHP;`
`  if (chr.emplType == EMPL_ROBOT)`
`    soldierSum += (0.5f + factor);`
`  else`
`    soldierSum += factor;`
`}`

`/* first factor is the amount of actors on each side */`
`numbers = soldierSum / (float)ccs.battleParameters.aliens;`
`/** @todo second factor is equipment */`
`balanceOfPowerIndex = min(1.0, numbers * difficulty->value);`

`for (i = 0; i < aircraft->teamSize) {`
`  const character_t *chr = &aircraft->acTeam[p]->chr;`
`  const float injuryChance = (1.0f - balanceOfPowerIndex);`
`  const float deathChance = 0.5 * (1.0f - balanceOfPowerIndex);`
`  const float healthLost = max(0.25f, frand() - 0.25f);`
`  const float liveCaptureChance = 0.1f;`
`  /** @todo MAX_SKILL is not correct here */`
`  const float increase = min(1.0, 1.0f / numbers) * MAX_SKILL;`
`  /** @todo */`
`}`

## My Comments

Proposal looks excellent to me, but please add a bonus for the number of
troops as well as the weight of HP. This will more accurately reflect
the advantage of numbers, i.e. 2 soldiers at 50% HP are more dangerous
than 1 at 100%. --[Winter](User:Winter "wikilink") 21:51, 20 September
2008 (UTC)