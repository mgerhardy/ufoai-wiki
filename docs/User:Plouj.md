# TODO

- make available port finding more robust (see NET_OpenIP() in
  src/ports/\*/net_\*.c)
- avoid the segfault when no available ports are found
- make UI drawing work better in widescreen resolutions
  - this requires a significant change in the GUI drawing system
- make the Linux installer handle 32bit and 64bit binaries in a logical
  and error resistant way
- fix resource loading code
  - order should be: filesystem -\> pk3 (sorted by name)
  - use files from 1base.pk3 if they are also in 0base.pk3
- improve the autotools building system to make it work in cygwin
- fix problems reported by autoreconf