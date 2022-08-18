## Geosoft

- 3\. our struct use the convention 3 with a prefix in lower case
  `class uiMyFunkyWidget`. Maybe we can use namespace, if we decide to
  use it. But while we have not updated part of the code with it we
  should use our current naming convention. Anyway, we can use both.
- 10, 11 more and more i dislike that way. IDE is quite nice now. It it
  not beautiful, displeasing, but if you need it to live, its ok
- 23, 24... no idea
- 31 i prefer `Color::RED`
- 34 what we have is ok, should we really need to update everything
  again? Easy to do anyway, then i dont care
- 36 no idea, it can be problematic when fast computation is need? but
  most of the time we can do it
- 37 i dont like that, i prefere less newline
- 38 i prefer TAB to align code, but i dont want special char in strings
  `"\t"` instead of `" "`, dont know what they talk about.
- 49 we are not making strong OOP software, then i dont care about this
  rule. struct or class is the same for me
- 51 i dislike: what's going on `int* x, y, z`; Is `y` a pointer to int?
  anyway i also dislike multi declaration, i prefer

<!-- -->

    int *x;
    int *y;
    int *z;

- 58 sorry i love break and continue
- 71 should be what we have now TAB=4 (it is what i use here)
- 75 i prefer `} else {`
- 82 i prefer not to use that
- 83 i prefer not
- 84 but `case 100:`
- 85 i dont see why
- 87, 88, 89... ugly!
- 92 but still use `/** */` for method, class... javadoc

## Google

need some week to check everything