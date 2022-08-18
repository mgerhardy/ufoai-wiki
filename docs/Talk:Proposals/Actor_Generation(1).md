This seems like you want to use a uniform probability distribution for
the actor stats. You just give a minimum and a maximum value and each
value within is equally likely. I don't think that this is a very good
choice. You get a very broad distribution with the average value beeing
exactly as likely as the minimum and the maximum. Moreover you have a
sharp cutoff.

I think most people are average and there are only a few who are much
better or worse than this average. To reflect this I suggest to use a
normal (gaussian) distribution and instead of giving a minimum and a
maximum value you would have to use a list with the average value and a
standard deviation. --[Camouflage](User:Camouflage "wikilink") 15:42, 30
January 2009 (UTC)

I included a table so all of you who are not so familiar with
probability distributions can compare the two distributions. The example
is for the strenght of a common soldier; p is a uniform probability
distribution with fixed minimum and maximum and each value within
equally likely. pn is a normal distribution with average value 20 (same
as for p) and a standard deviation of 5 (which is a bit smaller than the
standard deviation of p).

| str | p    | pn   |
|-----|------|------|
| 8   | 0.00 | 0.00 |
| 9   | 0.00 | 0.01 |
| 10  | 0.05 | 0.01 |
| 11  | 0.05 | 0.02 |
| 12  | 0.05 | 0.02 |
| 13  | 0.05 | 0.03 |
| 14  | 0.05 | 0.04 |
| 15  | 0.05 | 0.05 |
| 16  | 0.05 | 0.06 |
| 17  | 0.05 | 0.07 |
| 18  | 0.05 | 0.07 |
| 19  | 0.05 | 0.08 |
| 20  | 0.05 | 0.08 |
| 21  | 0.05 | 0.08 |
| 22  | 0.05 | 0.07 |
| 23  | 0.05 | 0.07 |
| 24  | 0.05 | 0.06 |
| 25  | 0.05 | 0.05 |
| 26  | 0.05 | 0.04 |
| 27  | 0.05 | 0.03 |
| 28  | 0.05 | 0.02 |
| 29  | 0.05 | 0.02 |
| 30  | 0.05 | 0.01 |
| 31  | 0.00 | 0.01 |
| 32  | 0.00 | 0.00 |

--[Camouflage](User:Camouflage "wikilink") 16:27, 30 January 2009 (UTC)

Wouldn't it be nice if this could be "upgraded" with armour-style
definitions, so aliens could have the strengths and weaknesses the
UFOpedia states? And maybe UGVs could use them as well.
--[DarkRain](User:DarkRain "wikilink") 02:46, 23 November 2009 (UTC)