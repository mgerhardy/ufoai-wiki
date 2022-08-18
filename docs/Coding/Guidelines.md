## General

- If you change a function prototype make sure that **all** other
  prototypes for **all** the ports out there are changed, too
  *(otherwise you will break the port)*
- Use ANSI C99, except in platform specific code, even then only use
  something else if you ABSOLUTELY have to.
- Use K&R style of coding (what, you DON'T own a copy?)
- C-style comments ONLY!
  **`/* comment */`**
- If you need to temporarily disable a chunk of code, use \#if 0 ...
  \#endif, rather than just a /\* comment \*/.
- One declaration per line please.
- Try to only include those headers that are really needed (to keep the
  compile times low when you change a header)
- Avoid using one big header for everything. Almost each C-file should
  get its own header someday.
- Guard headers with
  <dir under src>

  _\<filename without .h\>_H in capitals. For example
  ./src/client/cdaudio.h is guarded with:

<!-- -->

    #ifndef CLIENT_CDAUDIO_H
    #define CLIENT_CDAUDIO_H

    ...

    #endif /* CLIENT_CDAUDIO_H */

- remember to put a blank line at the end of the file (GCC will complain
  if you don't.)
- don't put more than one blank line at the end of the file (GIT will
  complain if you do.)
- All files must contain a GPL notification (google GPL or just lookup
  an existing file).
- Always use braces in if-else blocks. Doing anything else is
  error-prone. One line ifs are okay. E.g.

<!-- -->

    /* This is okay */
    if (x)
        printf("Blah");

    /* This may look okay, but can get very messy when you start nesting */
    if (x)
        printf("Meep");
    else if (y)
        printf("Moop");
    else

    /* This is the worst of all */
    if (x) {
        printf("A");
        if (z)
            printf("B");
        else if (j) {
            printf("X");
        } else
            printf("Z");
    } else if (y)
        printf("C");
    else
        printf("D");

- Feel free to use indent (Unix / Cygwin). Current command: indent -kr
  -l160 -bad -bap -ut -i4 -ts4 <filename>

### TABs

1.  Use TABs instead of spaces.
2.  Use a TAB-width of 4 characters (editor settings). Do NOT SAVE THE
    SPACES in the files, see first point.

### Long conditional expressions

1.  break before an operator
2.  indent the operator just enough to align the rest of the expression
    with its first half
3.  in most situations this means one space: \[space\]operator\[space\]
    becomes 4 characters

<!-- -->

        if ((to->armour && Q_strcmp(fItem->item.t->type, "armour"))
         || (to->extension && !fItem->item.t->extension)
         || (to->headgear && !fItem->item.t->headgear)) {
            return IA_NONE;
        }

If such conditionals are repeated in various places, make them a macro
or separate function.

### Whitespaces in function declarations, definitions and calls

These are guidelines about whitespace usage between the function name
and the left bracket that starts the argument list.

Omit it in the headers in function declarations:

    void prototype(void);

Include it in function definitions:

    void prototype (void)
    {
      /* implementation */
    }

Omit it in function calls:

    void someother (void)
    {
    [...]
      prototype();
    [...]
    }

This format makes it easy to find functions in the code. It also makes
the code easier to read.

### General function & variable names

- Function names look like: `CL_MyRandomFunction()`, where `CL` is the
  abreviation of the compilation unit (the C-file the function is
  located in). This includes `#define` macros that work like functions.
- Console vars look like this: `cl_lower_case`.
- All other variables should be written in camel case.

### Identifiers and names inside structs

There is alot of (deprecated) code where there are the following
variables defined inside a struct:

- `name` or `kurz` - ('kurz' is german for 'short') short
  string-identifier from the ufo-files.
- `title` - Translated full name.

They should not be used and replaced with the following:

- `id` - short string-identifier from the ufo-files. \[replaces `name`
  from above\]
- `name` - xxx \[replaces `title` from above\]
- `idx` - xxx

**Attention** has to be paid to the different meaning of the **`name`**
variable. Please try to not mix them up.

### Structures / Typedefs

Structures / typedefs are:

    typedef struct menuNode_s {} menuNode_t;

YES, you WILL typedef your structs! Structure members should be added by
one per line and should be documented properly. **Bad** example:

    typedef struct menuNode_s {
        int blah, a;
        int blahBlah;
    } menuNode_t;

For **good** one look into full example.

### Text being sent to the user

Any text being sent to the user needs to be written in English. Yes, in
English - not Polish English or German English. That means - start with
uppercase letter, end with dot. Bad:

- `CL_DisplayHudMessage(_("your soldier is dazed\n"), 2000);`

Ok:

- `CL_DisplayHudMessage(_("Your soldier is dazed.\n"), 2000);`

### Plural forms

Use ngettext function to handle plurals. It can select right form in
regard of item count. DO NOT prefix texts with _(). Usage:
ngettext("singular", "plural", cnt). See Full Example.

### Full Example

    /**
     * @file main.c
     * @brief Main source file.
     *
     * Contains the main() function and many associated functions and typedefs.
     */

    /*
     * All original material Copyright (C) 2002-2006 UFO: Alien Invasion team.
     *
     * This program is free software; you can redistribute it and/or
     * modify it under the terms of the GNU General Public License
     * as published by the Free Software Foundation; either version 2
     * of the License, or (at your option) any later version.
     *
     * This program is distributed in the hope that it will be useful,
     * but WITHOUT ANY WARRANTY; without even the implied warranty of
     * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
     *
     * See the GNU General Public License for more details.
     *
     * You should have received a copy of the GNU General Public License
     * along with this program; if not, write to the Free Software
     * Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
     *
     */

    /**
     * @brief Holds information about individual nodes in a menu.
     */
    typedef struct menuNode_s {
        int blah; /**< This is a documentation comment. */
        int a; /* armour */ /**< Calling this 'a' then putting a comment immediately after is just dumb. Don't do it; use meaningful names */
        int blahBlah; /**< The total number of blahs. */
    } menuNode_t;

    /**
     * @brief Does this and that
     * @return Returns blah if blub.
     */
    int Function (void)
    {

    }

    /* This is an ordinary C comment.
    If you encounter one of these you will need to update it to a full doxygen comment where appropriate.
    */
    int R_DrawStuff (void)
    {

    }

    /**
     * @brief The main function and program entry point.
     *
     * The line above is the brief description of the function below.
     * Anything after the blank line is the detailed description (these two lines).
     * @return Returns the interesting result.
     */
    int main (void)
    {
        int x;
        int y;

        if (x < y) {
            x *= y;
        } else if (x > y) {
            y = x;
        } else {
            printf("Blah!");
        }

        for (x = 10; x > 0; x--) {
            /* Do something interesting */
            printf(ngettext("Remain %i day\n", "Remain %i days\n", x), x);
        }

        return 0;
    }

## \#include rules

1.  Every c/cpp file includes its own header file first.
2.  A header file must include all the header files necessary to parse
    it. This goes hand in hand with the first guideline. I know some
    people try to never include header files within header files
    claiming efficiency or something along those lines. However, if a
    file must be included before a header file can be parsed, it has to
    be included somewhere. The advantage of including it directly in the
    header file is that we can always decide to pull in a header file
    we’re interested in and we’re guaranteed that it’ll work as is. We
    don’t have to play the “guess what other headers you need” game.
3.  A header file should have the bare minimum number of header files
    necessary to parse it. The previous rule said you should have all
    the includes you need in a header file. This rule says you shouldn’t
    have any more than you have to. Clearly, start by removing (or not
    adding in the first place) useless include statements. Then, use as
    many forward declarations as you can instead of includes. If all you
    have are references or pointers to a class, you don’t need to
    include that class’ header file; a forward reference will do nicely
    and much more efficiently.
4.  .h files should have exactly the same name as the corresponding .c
    file. (should be self-understood) (unlike files.c \<\> filesys.h)
5.  .c/.h pairs should have a unique name. (unlike common/bsp.c \<\>
    tools/ufo2map/bsp.c.)
6.  No .c without a .h except main(). Helps to prevent 'superincludes'.
    (unfortunately we have quite a lot of those)

The current UFO:AI code is **very** far away from complying to those
rules. But well, it's a start.

## Commit rules

To make the commit logs work better with some commands and filters, we
have a fixed format for the commit comments:

    * The first line summarises the effect of the commit. After this follows an empty line.

    * Details are written here. The above line is just the commit summary. And such
      a comment may also be on more than one line if the text is too long. But each subtopic
      should start with a * in front of it.
    * The newline between the summary and the details is needed.
    * Details are optional.

## Documenting code

Use [doxygen](doxygen "wikilink") to document code.

Doxygen comments are very much like Javadoc. The main exception is that
the comment for the file (At the top of the file) needs the `@file`
command, as shown in the example above.

Brief comments should describe WHAT something does, NOT how. For
example, a **good comment**.

    /**
     * @brief Calculates the chance to hit.
     * @param[in] skill <What skill is.>
     * @param[in] distance <What distance is.>
     * @return <What is returned in which case>
     */
    float ToHit (int skill, float distance)
    {
    }

And a **bad one** - it should be apparent from the code:

    /**
     * @brief Calculates the chance to hit by taking the skill, dividing it by the distance and multiplying by F.
     */
    float ToHit (int skill, float distance)
    {
    }

The detailed description should include enough detail to understand how
the function works, in the above example, the detailed description
should probably describe the factors involved in shooting, so that
someone testing the gameplay could experiment with a spreadsheet.

There is a doxygen config file to generate HTML documentation (latex
disable for now) for every typdef, function and non-local variable in
the entire source tree (except for the tools).

### Blank Documentation

Blank documentation is bad. Do **not** leave blank doxygen commands like
this:

    /**
     * @brief
     * @param
     * @sa
     */
    void someFunction (void)
    {
    ...
    }

There is no reason to do this. It hides the fact that this code is
undocumented. It might even confuse doxygen. If you do not want to
document code then don't even start.

### Code TODO's

Use the [doxygen](doxygen "wikilink") @todo command to mark TODO's in
the code. For example:

    /** @todo: make the numbers work here. */

Always remember that Doxygen's commands are case sensitive. @todo is
different from @TODO. The latter is not a valid command.

TODO: Needs to be more comprehensive.

## Preprocessor

Use **DEBUG** to surround statements that are not needed for the game
but are good for debugging purposes

` #ifdef DEBUG`
` dosomething();`
` #endif`

**PARANOID** surrounds some speed influencing checks for variable values
and overflows. Very good for debugging - statements enclosed by
**PARANOID** may slow down the game a lot.

` #ifdef PARANOID`
` dosomething()`
` #endif`

## Links

[Coding](Coding "wikilink")

[Category:Contribute](Category:Contribute "wikilink")
[Category:Coding](Category:Coding "wikilink")