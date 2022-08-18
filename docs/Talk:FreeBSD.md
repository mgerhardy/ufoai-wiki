we are using execinfo.h to determine whether the system has backtrace
creation support - if this isn't working for freebsd the assumption that
execinfo.h and backtrace function are going hand in hand is just wrong
and should be fixed.

the amd64 stuff was added to the configure script


--[Mattn](User:Mattn "wikilink") 15:31, 31 July 2010 (UTC)