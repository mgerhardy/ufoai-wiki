## C++

Now that we have enabled C++, I've taken the task to organize the
discussion about which coding guidelines we'll need for C++. My
favourite reading regarding this aspect is John Lakos "Large scale C++
projects". Ouote: "It doesn't matter which style you choose; it's
important to use the chosen style consistantly."
UFO:AI is only medium scale. But it doesn't hurt to comply to those
rules. --[Duke](User:Duke "wikilink") 00:28, 11 April 2012 (SAST)

### Participants

This should be discussed among those who consider themselves as 'current
permanent contributors'. It's all about how \*we\* want the code to look
like. The idea is to restrict the voting to those who have to suffer the
most. As there are more coding styles than coders in the world, this
strategy avoids endless discussions. I went through that several times,
believe me :(
Invitations go out to (alphabetically):
[Sandro](User:Sandro "wikilink"), [bayo](User:bayo "wikilink"),
[Duke](User:Duke "wikilink"), [geever](User:geever "wikilink"),
[mattn](User:mattn "wikilink")
...and as a 'technical advisor' [Tron](User:Tron "wikilink")
Hmm. Do we really have that few ? :(

### Strategies

We could

- discuss and write our own guidelines from scratch (oh no)
- adopt some published guideline (and eventually modify it a bit)
- find a checker and/or beautifier tool and accept what it does.

I vote for the second option because the first would mean reinventing
the wheel and I don't think any tool can check all the rules.

### Suggestion

Googling for "coding guidelines C++" we find lots of them. I checked a
few of them and found this one:

- Duke's comment: With a few exceptions it describes pretty much what I
  did intuitively in the past. So I like it. The exceptions are rules \#
  28, 36, 37, 38, 40, 58, 62, 71 and 83. My favourite rule is \#89. But
  let's see what you guys come up with.
- [Bayo's comments](Talk:Coding/Guidelines/bayo "wikilink")

### Dev's discussion

- 3
  - bayo: our struct use the convention 3 with a prefix in lower case
    `class uiMyFunkyWidget`. Maybe we can use namespace, if we decide to
    use it. But while we have not updated part of the code with it we
    should use our current naming convention. Anyway, we can use both.
  - Duke: the lowercase prefix would render rules 4 and 6 somewhat
    senseless. Also, except for the ui we don't have a consistent
    convention afaik.
    - Then ok for this rule, i thinking we have own rules about that.
      But then it is really need to use namespace, at least for "ui".
      [Bayo](User:Bayo "wikilink") 10:26, 21 April 2012 (SAST)
      - Uhm, don't get me wrong. Some subsystem-prefix can be useful.
        But it shouldn't start with lowercase. So it's "Ui" or "Uis",
        and "Cpg" for campaign maybe. But we should have a discussion
        what our subsystems are in the first
        place.--[Duke](User:Duke "wikilink") 23:23, 23 April 2012 (SAST)
  - geever: Our type names are quite much recognizable, not a standard
    though. I would rather not use prefixes, but if we wanna prefix
    types, use the prefix we have for functions "UI_" and "CP_". I
    don't really like the "CpgMission_t" names, sound weird.
- 11
  - bayo: more and more i dislike that way. IDE is quite nice now. It it
    not beautiful, displeasing, but if you need it to live, its ok
  - Duke: in general I dislike all those single letter pre- and
    suffixes. But the sideeffect for setters has some charm
  - geever: definietly NO. it's horror
  - intermediate result: we all dislike them. So does anyone have an
    alternative suggestion for the 'setDepth'-example ?
  - mattn: in radiant we used _name, not name_ - and it has advantages
    to do it that way. Yes, IDEs support you, but you see which is a
    member variable, and which is a local var or function parameter. So
    i would vote for doing _name.
- 14
  - geever: I don't like long variable names at all, they give me more
    possibility to mistype them. :) Keep them as short as they can
    (while they are still understandable ofc.)!
    - In respect to that rule, I understand 'long variable name' as
      anything longer then 1-2 letters. So your statement is no
      contradiction to that rule.--[Duke](User:Duke "wikilink") 22:12, 9
      July 2012 (SAST)
  - mattn: They should not be too short, and IDEs are supporting one
    well enough with auto completion. But i agree, we should not make
    then too long.
- 28
  - Duke: I agree with the 2nd half of that rule. But I prefer "init"
    instead of "initialize" and "calc" instead of "calculate"
    - I usually prefer full names. Much more readable.
      [Bayo](User:Bayo "wikilink") 10:26, 21 April 2012 (SAST)
      - Oh, I only use that for maybe a dozen \*standard\* abbreviations
        like the above. --[Duke](User:Duke "wikilink") 22:14, 23 April
        2012 (SAST)
  - geever: vote for short names (I wrote this to points 18 and 20, but
    it has a dedicated rule :) )
    - Do you mean a fixed list of say 12 common short forms like "init"
      or do you want a general 'licence to abbreviate' ?
      --[Duke](User:Duke "wikilink") 22:28, 9 July 2012 (SAST)
- 34
  - mattn: on the long run, it would be cool to have this - just to
    unify with radiant, but only for classes. not for the other "normal"
    c files.
- 36
  - bayo: no idea, it can be problematic when fast computation is need?
    but most of the time we can do it
  - Duke: Disagree with that rule. Simple getters and setters should
    imho be inlined anyway and thus stay in the .h file.
    - The google style has something nice about it. .
      [Bayo](User:Bayo "wikilink") 10:26, 21 April 2012 (SAST)
  - geever: However sometimes I find our cpp files overstuffed with
    code, splitting everything to files would make our life a nightmare
    -- even for you who use IDEs
    - Sorry, didn't understand that. Please
      elaborate.--[Duke](User:Duke "wikilink") 22:49, 9 July 2012 (SAST)
  - Tron:
- 37
  - bayo: i dont like that, i prefere less newline
  - Duke: Disagree. 80 chars stems from punchcard. We have reached the
    age of widescreens and zoomable editors. And we don't print the
    code, do we ? Suggestion: The code without the comments \*should\*
    not be wider than 60 chars (think of editing on a smartphone), the
    whole line \*must\* end before 140 chars are reached.
    - BTW i dont like coment in the same line.
      [Bayo](User:Bayo "wikilink") 10:26, 21 April 2012 (SAST)
  - geever: disagree, I won't count characters when typing
  - our vote: drop rule
  - mattn: drop - but i agree with bayo - comments above the line, not
    after it.
- 39
  - geever: indent rest of the line by one (tab) but don't pad the code
    with spaces to the matching bracket like in the example
- 40
  - mattn: pragma once is ok, too imo.
- 45
  - geever: not sure if it should be done every time... annoying
  - Duke: use casts only where it is needed to avoid a -Wall warning.
    btw do we need to use static_cast if we don't use RTTI ?
  - bayo:
- 46
  - geever: our previous (maybe non-documented) rule was to initialize
    the variables the closest to their use, and I feel it more
    appropriate. However it is a good question where to declare
    variables...
- 49
  - bayo: we are not making strong OOP software, then i dont care about
    this rule. struct or class is the same for me
  - Duke: it will take ages until we comply to this rule; however, it
    should be the goal.
  - geever: acceptable
  - Duke: new suggestion: make it a 'should' for migrated structs and a
    'must' for new classes.
- 60
  - geever: I remember a rule or recommendation to use
        for (;;) {}

    instead. If I'm right, we have already changed some of our loops to
    that..

    - We have about the same amount of "while(1)" and "for(;;)". Only
      very few "while(true)"--[Duke](User:Duke "wikilink") 23:39, 9 July
      2012 (SAST)
- 61
  - geever: I think it actually makes understanding harder as you need
    to track more variables in head while debugging.
    - I completely disagree. If you can assign a meaningful name to a
      non-trivial condition, it will enhance readability AND help
      debugging a lot. Try it.--[Duke](User:Duke "wikilink") 23:39, 9
      July 2012 (SAST)
  - mattn: i agree to duke, it can make reading code a lot easier, BUT:
    some statements must not be evaluated because they are not needed
    due to the false value of an earlier expression. Keep that in mind
    while extracting stuff.
- 64
  - geever: I like shorter code, however splitting helps debugging, so I
    can accept it
- 70
  - geever: We have NULL almost everywhere, and it tells me it's a
    pointer, so I would rather use NULL than 0.
    - mattn: NULL is not valid in the c++ context in every case.
      foo(NULL) calls foo(int). which is not always what you want.
- 72
  - geever: first example as we have them now
- 77
  - geever: gcc suggests `for (init; condition; update) {}` and feel it
    better. With a lone semicolon I have a feeling that someone
    accidentally cut&pasted the call, instead of copy&pasting.
  - Duke: somewhat depends on the outcome of rule \#60.
  - {} is less error prone. missing the semicolon will execute the next
    line as loop statement. So no, i disagree to this rule.
- 80
  - geever: our current rule suggest writing cases on the same level as
    the switch itself.
- 82
  - bayo: i prefer not to use that
  - Duke: I like it, coz it saves a line with just a '}'
    - but you dislike `} else {` cause it save a line... Anyway my point
      is "put a block everywhere cause it is safer", especially when you
      hack the code. [Bayo](User:Bayo "wikilink") 10:26, 21 April 2012
      (SAST)
      - No, I like "else {" because the if aligns with the else. The 'is
        safer'-argument is strong. And I can easily live with
        it.--[Duke](User:Duke "wikilink") 23:02, 23 April 2012 (SAST)
  - geever: I code like this ( if possible, not in Perl ;( )
- 87, 88, 89...
  - bayo: ugly!
  - Duke: beautiful !
    - Then, else the space, you agree with an if in 1 line, or a case in
      1 line? [Bayo](User:Bayo "wikilink") 10:26, 21 April 2012 (SAST)
      - I general, I don't. But if it's a \*series\* of very similar
        ifs, resembling a table, it can increase readability a lot.
        --[Duke](User:Duke "wikilink") 21:55, 23 April 2012 (SAST)
  - geever: it's horrible. It also hurts our current whitespace rules.
  - mattn: as you know - i'm a whitespace killer, i don't like this rule
    at all. and it does not improve readability imo. one newline is
    enough to mark a paragraph. there is somewhere a discussion for
    latex about this topic, too. and a paragraph is one newline (well,
    two - one empty line)
- 92
  - bayo: but still use `/** */` for method, class... bref, for the
    javadoc
  - Duke:
  - geever: we should use the C-ish ones only (and doxygen notation), we
    can still disable code with the good old `#if 0`

`/* one lined */`
`/*`
` * Some important`
` * multiline`
` */`

- - mattn: good old /\*\* \*/

### mattn's decision

- 10
  - bayo: more and more i dislike that way. IDE is quite nice now. It it
    not beautiful, displeasing, but if you need it to live, its ok
  - Duke: I'm insecure here.
  - geever: dislike
  - our vote: drop rule
  - mattn:
- 23, 24...
  - bayo: no idea
  - Duke: imho we don't need a convention for that, so omit those two
    rules
    - Ok, we can take it as a "may". [Bayo](User:Bayo "wikilink") 10:26,
      21 April 2012 (SAST)
  - geever: 24: we use Idx at multiple locations already. we can ommit
    them
  - our vote: drop rule
  - mattn:
- 31
  - bayo: i prefer `Color::RED`
  - Duke: Color::RED looks a tad nicer, but requires discipline.
    COLOR_RED is forced by the compiler ;)
  - geever: I like our prefixed constants either
  - our vote: COLOR_RED
  - mattn:
- 34
  - bayo: what we have is ok, should we really need to update everything
    again? Easy to do anyway, then i dont care
  - Duke: imho .h and .cpp are ok.
  - geever: .h and .cpp
  - our vote: .h and .cpp
  - mattn:
- 38
  - bayo: i prefer TAB to align code, but i dont want special char in
    strings `"\t"` instead of `" "`, dont know what they talk about.

    Bayo, that rule is not about "\t". But that should be avoided
    too.--[Duke](User:Duke "wikilink") 00:39, 19 April 2012 (SAST)
  - Duke: NO page breaks in the source. But I prefer tabs over spaces.
  - geever: our indent rule is good enough: use tabs, no page breaks
  - our vote: no page breaks, but tabs instead of spaces
  - mattn:
- 40
  - Duke: Sure we need include guards like that. But our convention
    should be more like \[DIR_\[SUBDIR_\]\]CLASS_H
    - Yes, still use what we have. [Bayo](User:Bayo "wikilink") 10:26,
      21 April 2012 (SAST)
  - geever: what we have now is good enough (don't need to
    overcomplicate it)
  - our vote: stick with \[FILENAME\]_H, prefix with
    \[DIR_\[SUBDIR_\]\] if not unique
  - mattn:
- 51
  - bayo: i dislike: what's going on `int* x, y, z`; Is `y` a pointer to
    int? anyway i also dislike multi declaration, i prefer

<!-- -->

    int *x;
    int *y;
    int *z;

- - Duke: if and only if we have an additional rule that requires 'one
    declaration per line', I'd prefer

<!-- -->

    int* x;
    int* y;
    int* z;

- - geever: I prefer
        int *x;

    and we should have a one declaration per line rule. We have it now.

<!-- -->

- - our vote:
        int *x;

I think we made a mistake here. As you all know, I have already changed
a lot of lines to the above style. But I ran into problems:

    const teamDef_t* const td;
    const teamDef_t *const td;  // ??
    const teamDef_t * const td  // ????
    // and
    typedef aseFace_t* aseFacesIter_t;
    typedef aseFace_t *aseFacesIter_t;  // doesn't look right for me

So I strongly recommend to use the "int\* x;" style.
--[Duke](User:Duke "wikilink") 23:19, 23 May 2013 (CEST)

- - Sandro's comments (copied from IRC by Duke)

I still like type \*ptr syntax. Reason: C types work this way: name some
type and declare what you want to do with it. typedef works in somehow
backwrds waay, but follows the same logic. type\* ignores that logic,
see the (in)famous int\* x,y,z; example. Anyway, const problem can be
fixed in most cases by switching to references :) since references are
const by definition in language standard

- - Sandro, I doubt that we can switch to references in 'most' cases.
    'Many' sounds more realistic to me. But however many they are, we
    don't have a solution for the const problem in the remaining
    cases.--[Duke](User:Duke "wikilink") 22:02, 30 May 2013 (CEST)

<!-- -->

- - mattn:

Indeed, this was a mistake - everything that defines a type of a
variable should be grouped. This is also useful for having typedefs.
Imagine the following:

`someType_t *ptr;`

now you convert to:

`typedef someType_t* someTypePtr;`
`someTypePtr ptr;`

Imo it's wrong to place a pointer of reference char to the variable - it
belongs to the type.

`const someType_t* const ptr;`
`someType_t* const ptr;`
`someType_t* ptr;`
`someTypePtr ptr;`
`typedef SharedPtr`<someType_t>` SomeTypePtr;`
`SomeTypePtr ptr(new someType_t());`
`const someType_t& ref = getSomeRef();`
`someType_t& ref = otherVar;`

--[Mattn](User:Mattn "wikilink") 09:06, 29 May 2013 (CEST)

- 58
  - bayo: sorry i love break and continue
  - Duke: me too
  - geever: me too
  - our vote: drop rule
  - mattn:
- 62
  - Duke: as the handling of the exception is usually much shorter, it
    should be handled first
    - I think it is not a strong rule anyway.
      [Bayo](User:Bayo "wikilink") 10:26, 21 April 2012 (SAST)
  - geever: drop this rule
  - our vote: drop rule
  - mattn:
- 71
  - bayo: should be what we have now TAB=4 (it is what i use here)
  - Duke: Yes. TAB=4. As we have dropped the column width of 80, we can
    afford that.
  - geever: one tab (the tabsize is doesn't really matter as we're not
    converting them to spaces)
  - our vote: TAB=4
  - mattn:
- 75
  - bayo: i prefer `} else {`
  - Duke: i prefer `else {`, but don't care much
    - Yes, both are readable for me [Bayo](User:Bayo "wikilink") 14:21,
      21 April 2012 (SAST)
  - geever: I vote for `} else {`.
  - our vote: `} else {`
  - mattn:
- 83
  - bayo: i prefer not
  - Duke: I hate it
  - geever: I hate it too
  - our vote: drop rule
  - mattn:
- 84
  - bayo: but `case 100:`
  - Duke: agree with bayo
  - geever: agree, use our current rule
  - our vote: ok, but `case 100:`
  - mattn:
- 85
  - bayo: i dont see why
  - Duke: Dislike it. Over-complicated. Foo(bar) is fine for me.
  - geever: agree with you: Foo(bar)
  - our vote: drop rule
  - mattn:

### Other things to avoid

The google styleguide has an interesting section "Other C++ features"
about things NOT to use that should be discussed.

## Struct

`typedef struct menuNode_s {`
`   int blah; /**< This is a documentation comment. */    `
`   int a; /* armour */ /**< Calling this 'a' then putting a comment immediately after is just dumb. Don't do it; use meaningful names */`
`   int blahBlah; /**< The total number of blahs. */`
`} menuNode_t;`

Can we avoid thing like **int a** in structs. The code looks often hard
to understand. Here we can use *armour*. I especially thing about the
inventory code. [Bayo](User:Bayo "wikilink") 11:21, 3 September 2010
(UTC)