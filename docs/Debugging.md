## General

See also [Coding/Debug commands](Coding/Debug_commands "wikilink").

## Windows

### Code::Blocks

- [Compile](Code::Blocks "wikilink") the game in debugging mode
  - To add debugging symbols in Windows use in C::B the Build target,
    through the build menu:
        windows_debug

    instead of

        windows
- The [Code::Blocks](Code::Blocks "wikilink")-installation includes .
- Integrated debugging
  - Use *+set vid_fullscreen 0 +set vid_grabmouse 0 +set developer 1* as
    program arguments
  - Just select the debugging option from the menu - you will get a
    backtrace and so on after the game crashed
- Manual debugging
  - You should add the [Code::Blocks](Code::Blocks "wikilink")
    installation folder to your environment path variable (most likely )
  - To start UFO:AI in the debugger you need to enter the
    windows-console (Start-\>Execute-\>cmd.exe)
  - Enter the UFO:AI folder and type
        gdb ufo.exe
  - Now you are in the debug console of `gdb`
  - Run the game with
    - run +set vid_fullscreen 0 +set vid_grabmouse 0

    - or with
          run +set vid_fullscreen 0 +set vid_grabmouse 0 +set developer 1

      if you need the debug-messages from within the code.
  - After a crash you can toggle via to gdb console.
  - To locate the problem, type
        bt full

    which generates a backtrace and displays the values of local
    variables.
- Submit this information to the [bugtracker](Bugs "wikilink").

### Dr.MinGW

Dr.MinGW is a JIT debugger (Just-In-Time-Debugger) - see the
[homepage](http://jrfonseca.planetaclix.pt/projects/gnu-win32/software/drmingw/index.html)
for more information about it.

### gdb on Windows

Yes, also works under Windows. The usage is the same as shown in the
[\#Linux](#Linux "wikilink") and [\#Useful gdb
stuff](#Useful_gdb_stuff "wikilink") section below.

*Add instructions here on how to make gdb work. It seems to be incldued
in Dev-Cpp, but not in others - and even in Dev-Cpp you need to set
paths.*

## Linux

### Disable ingame backtrace

    ./configure --disable-execinfo

### gdb

- You have to have installed (included in the Codeblocks package).
- Add the gdb.exe to your path.
- [Compile](Compile_for_Linux "wikilink") the game in debugging mode
  (standard).
- Go to directory where `ufo` binary is located (see [directory
  tree](Directory_tree "wikilink")).
- Run
      gdb ufo

  from the commandline.
- Now you are in the debug console of `gdb`
- Run the game with
  - run +set vid_fullscreen 0 +set vid_grabmouse 0

  - or with
        run +set vid_fullscreen 0 +set vid_grabmouse 0 +set developer 1

    if you need the debug-messages from within the code.
- After a crash you can toggle via ' to gdb console.
- Type
      bt full

  to generate a backtrace and locate the problem.
- Copy the output in the console and submit to the
  [bugtracker](Bugs "wikilink").

Visit [this site](http://www.dirac.org/linux/gdb/index.php) for a more
in-depth gdb tutorial.

#### Generate core dumps

You can also generate core dumps from a running process - attach gdb to
the process, type and detach again. Now you have the core file for later
debugging.

#### Breakpoints

There are several commands to set breakpoints via gdb:

-

-

To remove them type:

-

-

-


Remove all breakpoints

-


Remove the ith breakpoint

Type to get a list of all breakpoints

#### Inspect variables

You can use or the abbrevation to print the content of the variable .
You can also print structures by typing .

accepts some format parameters:

- o = octal
- x = hex
- d = decimal
- u = unsigned decimal
- t = binary
- f = float
- a = address
- c = char

Use them via

#### Other useful commands

- To find out where you currently are type the command:

- To print some source around the current location type:

- Execute a single line in the program. If the current statement calls a
  function, the function is single stepped.

- Execute a single line in the program but treat function calls as a
  single line. This command is used to skip over function calls.

- To log output to a file, start by entering

`set logging file `<filename>

when ready to start logging, enter

`set logging on`

usually you will want to enter to generate & log the backtrace.

### valgrind

Use [valgrind](valgrind "wikilink") to detect and fix memory
[bugs](bugs "wikilink"). There is a script that might help you in named
. It will create a logfile in trunk of the output.

### bugle

[bugle](http://bugle.sourceforge.net/) can be used to trace
[OpenGL](OpenGL "wikilink") calls, hunt for unchecked OpenGL errors,
take video shots, and do plenty of other OpenGL-related debugging.

e.g. to get a full trace of OpenGL calls:

    BUGLE_CHAIN=trace LD_PRELOAD=/path/to/libbugle.so ufo +set gl_driver /path/to/libbugle.so

## glibc backtrace

The glibc feature for producing stacktraces is used in UFO, too - to get
meaningful output from the printed stackstrace you can use the addr2line
command from the binutils package.

## Useful gdb stuff

### Hints

- Use tab for command and variable completion''

- stops the program (use or to continue the execution

### Commands


Prints information about the gdb command


Prints code from current active position (useful to set breakpoints)


Handle breakpoints. Type to gdb console to get information. Example:
**break 184 if (status == 0)**

**b CL_ParticleRun2** will e.g. set a breakpoint to the function
*CL_ParticleRun2*


Sets a watchpoint. The main difference between watch and breakpoints is
that a breakpoint was set for a specific line - and a watchpoint can get
active on every line - it only needs it's condition to get true.
Example: **watch (varname \> 1024)**


Prints the value of a variable to gdb console (see )


Prints a value of a variable to gdb console (see ). If variable is a
pointer you can dereferencing it by typing  - like in C. You can even
assign a value to a var by typing **print \[varname\] = \[value\]**


Prints the type (typedef or struct) of the given variable name


Prints the backtrace


Continue the game execution

### Links

- [GDB documentation](http://www.gnu.org/software/gdb/documentation/)

[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")