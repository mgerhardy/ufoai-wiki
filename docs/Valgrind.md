## General

You can have a look at this howto to learn how to handle valgrind:
[howto](http://www.faqs.org/docs/Linux-HOWTO/Valgrind-HOWTO.html). You
can also use the valgrind.sh script located in . It will create a
logfile in the UFO:AI root dir.

## Compiling

Download [valgrind](http://valgrind.org/downloads/current.html) and
[callgrind](http://kcachegrind.sourceforge.net/cgi-bin/show.cgi/KcacheGrindDownload)

    tar -xjf valgrind-3.1.1.tar.bz2
    tar -xjf callgrind-0.10.1.tar.bz2

after uncompressing enter your new valgrind dir and type

    ./configure --prefix=/usr
    make
    make install

do exactly the same for **callgrind** and you are ready to go.

## Examples

### Generate callgraph

To generate a callgraph for kcachegrind you can use the commandline

    callgrind --dump-instr=yes --trace-jump=yes ./ufo

### Exclude some warnings

Valgrind will find many errors - most of them will be in the libs of
your distribution. To filter these errors (as they are not UFO:AI
releated - at least not directly) you can use the
`--gen-suppressions=no|yes|all` parameter

    valgrind --gen-suppressions=all ./ufo

will generate many suppressions that you can copy into a seperate file -
e.g. *suppressions.ufo*. Now you are able to run *valgrind* again - but
this time without the error messages that are not UFO:AI related.

    valgrind --suppressions=suppressions.ufo

NOTE: A suppression is enclosed in braces, e.g.

    {
       s1
       Memcheck:Cond
       obj:/lib/ld-2.3.6.so
       obj:/lib/tls/i686/cmov/libc-2.3.6.so
       obj:/lib/ld-2.3.6.so
       fun:_dl_open
       obj:/lib/tls/i686/cmov/libc-2.3.6.so
       obj:/lib/ld-2.3.6.so
       fun:__libc_dlopen_mode
       fun:__nss_lookup_function
       obj:/lib/tls/i686/cmov/libc-2.3.6.so
       fun:__nss_group_lookup
       fun:getgrnam_r
       fun:getgrnam
    }

    {
       s2
       Memcheck:Cond
       obj:/lib/ld-2.3.6.so
       obj:/lib/tls/i686/cmov/libc-2.3.6.so
       obj:/lib/ld-2.3.6.so
       fun:_dl_open
       obj:/lib/tls/i686/cmov/libc-2.3.6.so
       obj:/lib/ld-2.3.6.so
       fun:__libc_dlopen_mode
       fun:__nss_lookup_function
       obj:/lib/tls/i686/cmov/libc-2.3.6.so
       fun:__nss_group_lookup
       fun:getgrnam_r
       fun:getgrnam
    }

## External links

- [valgrind](http://www.valgrind.org/)

[Category:Coding](Category:Coding "wikilink")