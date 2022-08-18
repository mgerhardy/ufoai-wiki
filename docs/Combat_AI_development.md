## Using AI updates in 2.3

Most of the updates in the development trunk are limited in the g_ai.c
file. This means that you can \*probably\* use it for the 2.3 version
and check out the current status. Ask in the IRC channel or the AI
duscussion thread if you are not sure.

## Changes in trunk AI by version

- 30780: Dodon's patch for AI_HideNeeded & AI_FighterCalcBestAction
  brings hiding mechanics in line with the rest of the code. Immediate
  result is (almost) fearless aliens. More often than not an alien will
  opt to take another shot than to hide, and only severily demoralized
  aliens will opt to cower. Further development needed to make them less
  suicidal.

<!-- -->

- sometime before 31041 in both trunk and 2.3 branch. I've introduced a
  hideous segfault/assert error. 31041+ fixes that. And to think that
  broken patch didn't even introduce anything new...