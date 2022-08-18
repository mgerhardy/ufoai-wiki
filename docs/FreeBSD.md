## FreeBSD port

- FreeBSD port for UFO:AI-2.3

  - Makefile: adjust the do-install target, port compiles and ufo can be
    run within the ufoai23/work/ufoai-2.3-source directory

  - distinfo

  - pkg-descr

  - update pkg-plist: languages and other added files/dirs

  - files/pkg-message.in

  - files/run-sh.in: needed?

<!-- -->

- FreeBSD port for UFO:AI-2.4-devel: Fetch sources from svn

  - "make svn" fetches the revision specified with \${PORTVERSION}

  - change to interactive mode (-\>"make svn 31071")

  - Makefile: adjust the do-install target, port compiles and ufo can be
    run within the ufoai-devel/work/trunk directory

  - distinfo generated with "make makesum" inside "make svn"

  - pkg-descr

  - update pkg-plist: languages and other added files/dirs

  - files/pkg-message.in

### UFO:AI 2.3

BSD Licence for the portfiles, which are based upon ufoai-2.2.1 port.

#### ufoai23/Makefile (draft)

    # New ports collection makefile for:    ufoai
    # Date created:     2006-09-03
    # Whom:         Jose Alonso Cardenas Marquez <acm>
    #
    # $FreeBSD: ports/games/ufoai23/Makefile
    #

    PORTNAME=   ufoai
    PORTVERSION=    2.3
    CATEGORIES= games
    MASTER_SITES=   SF/${PORTNAME}/UFO_AI%202.x/${PORTVERSION}
    DISTNAME=   ${PORTNAME:S/$/-/}${PORTVERSION}
    DISTFILES=  ufoai-${PORTVERSION}-source.tar.bz2 ufoai-${PORTVERSION}-data.tar
    DIST_SUBDIR=    ${PORTNAME}

    #LATEST_LINK=   ufoai23

    MAINTAINER= ports@FreeBSD.org
    COMMENT=    A strategy game featuring tactical combat

    LIB_DEPENDS=    vorbis:${PORTSDIR}/audio/libvorbis \
            jpeg.11:${PORTSDIR}/graphics/jpeg \
            png.6:${PORTSDIR}/graphics/png \
            curl:${PORTSDIR}/ftp/curl \
            theora:${PORTSDIR}/multimedia/libtheora \
            xvidcore:${PORTSDIR}/multimedia/xvid \
            gtkglext-x11:${PORTSDIR}/x11-toolkits/gtkglext

    # Not needed anymore, after merging ufoai-data to ufoai23?
    #RUN_DEPENDS=    ${LOCALBASE}/share/${PORTNAME}/default.cfg:${PORTSDIR}/games/ufoai-data

    # pk3 files decompression
    EXTRACT_DEPENDS=unzip:${PORTSDIR}/archivers/unzip
    USE_GL=     yes
    USE_SDL=    sdl mixer ttf image
    USE_OPENAL= al
    # UFORadiant needs these. Without UFORadiant no tactical missions.
    # (sic!, maybe we can configure this without so much dependencies)
    USE_GNOME=  gtk20 glib20 gtksourceview2 libxml2
    USE_GETTEXT=    yes
    GNU_CONFIGURE=  yes
    USE_GMAKE=  yes
    CONFIGURE_ARGS+=    --enable-release=yes

    # portlint warning for CONFIGURE_ENV+
    CONFIGURE_ENV+=     LDFLAGS="-L${LOCALBASE}/lib ${PTHREAD_LIBS}" \
                CFLAGS="${CFLAGS} -I${LOCALBASE}/include" \
                CPPFLAGS="-I${LOCALBASE}/include ${PTHREAD_CFLAGS}"

    DATADIR=    share/${PORTNAME}
    SUB_FILES=  pkg-message

    # source-file extracts here:
    WRKSRC=     ${WRKDIR}/${PORTNAME:S/$/-/}${PORTVERSION}-source
    UFO_DIR=    ${PREFIX}/lib/${PORTNAME}
    UFO_FILES=  ufo

    # ufoai.xpm resides in debian/ufoai.xpm
    # portlint doesn't want the false variable..
    DESKTOP_ENTRIES=    "UFO:AI" "A squad-based tactical strategy game" \
                "${DATADIR}/ufoai.xpm" \
                "ufo" "Application;Game;StrategyGame;" \
                false

    OPTIONS=        SERVER  "Install dedicated server"  on \
                UFO2MAP "Install UFO tools" on \
                UFORADIANT "Install UFORadiant mapeditor"     off \

    .include <bsd.port.pre.mk>

    # Can be removed, if fixed in configure.ac upstream
    .if ${ARCH} == "amd64"
    CONFIGURE_TARGET?=x86_64-portbld-freebsd${OSREL}
    .endif

    .if !defined(WITHOUT_SERVER)
    CONFIGURE_ARGS+=    --enable-dedicated
    UFO_FILES+= ufoded
    PLIST_SUB+= UFOSERVER=""
    .else
    CONFIGURE_ARGS+=    --disable-dedicated
    PLIST_SUB+= UFOSERVER="@comment "
    .endif

    .if !defined(WITHOUT_UFO2MAP)
    CONFIGURE_ARGS+=    --enable-ufo2map
    UFO_FILES+= ufo2map
    PLIST_SUB+= UFO2MAP=""
    .else
    CONFIGURE_ARGS+=    --disable-ufo2map
    PLIST_SUB+= UFO2MAP="@comment "
    .endif

    .if !defined(WITHOUT_UFORADIANT)
    # I'm not sure, if --enable-uforadiant should be here or in the global args
    CONFIGURE_ARGS+=    --enable-uforadiant
    UFO_FILES+= uforadiant
    PLIST_SUB+= UFORADIANT=""
    .else
    CONFIGURE_ARGS+=    --enable-uforadiant
    PLIST_SUB+= UFORADIANT="@comment "
    .endif


    post-patch:
    # Unpacking pk3 files (from ufoai-data Makefile)
        @cd ${WRKDIR}/base && \
            ${FIND} * -type f -exec ${UNZIP_CMD} "{}" -d ${WRKSRC}/base \;

    # Maybe set an option to let the user choose, if he wants to make the pk3 files, install the ones from data.tar or without pk3
        @${RM} ${WRKDIR}/base/*.pk3

    # Resolve name collision with jpeg-8 amd API png
    # Nukama: still needed in 2.3?
    #   ${REINPLACE_CMD} -e 's|jpeg_mem_src|local_jpeg_mem_src|' \
    #       -e 's|png_set_gray_1_2_4_to_8|png_set_expand_gray_1_2_4_to_8|' \
    #       -e 's|png_check_sig(PngFileBuffer.buffer, 8)|!png_sig_cmp(PngFileBuffer.buffer, 0, 8)|' \
    #       ${WRKSRC}/src/client/renderer/r_image.c \
    #       ${WRKSRC}/src/tools/ufo2map/common/imagelib.c

    pre-install:
    #.  for FILE in ${UFO_FILES}
    #       @${ECHO} "#!/bin/sh" > ${WRKDIR}/${FILE}
    #       @${ECHO} "cd ${PREFIX}/${DATADIR} || exit 1 " >> ${WRKDIR}/${FILE}
    #       @${ECHO} "exec ${PREFIX}/${DATADIR}/${FILE} \"$$@\"" >> ${WRKDIR}/${FILE}
    #.  endfor

    post-build:
        @cd ${WRKSRC} && ${GMAKE} lang

    # UFORadiant Mapeditor doesn't work yet (with openal-soft I can start it, with some errors..)
    .if !defined(WITHOUT_UFORADIANT)
        @cd ${WRKSRC} && ${GMAKE} uforadiant
    .endif

    do-install:
    #   @${MKDIR} ${UFO_DIR}/base/i18n
    #.  for FILE in ${UFO_FILES}
    #   @${SED} \
    #       -e 's|@UFODIR@|${UFO_DIR}|' \
    #       -e 's|@APP@|${FILE}|' \
    #       ${FILESDIR}/run.sh.in > ${WRKDIR}/${FILE}
    #       ${INSTALL_PROGRAM} ${WRKSRC}/${FILE} ${UFO_DIR}
    #       ${INSTALL_SCRIPT} ${WRKDIR}/${FILE} ${PREFIX}/bin
    #.  endfor

    #       ${INSTALL_PROGRAM} ${WRKSRC}/base/game.so ${UFO_DIR}/base
    #
    #   @cd ${WRKSRC}/base/i18n && \
    #       ${FIND} * -type d -exec ${MKDIR} "${UFO_DIR}/base/i18n/{}" \; && \
    #           ${FIND} * -type f -exec ${INSTALL_DATA} "{}" "${UFO_DIR}/base/i18n/{}" \;
    #   ${LN} -s ${PREFIX}/${DATADIR}/* ${UFO_DIR}/base

    post-install:
        @${CAT} ${PKGMESSAGE}

    .include <bsd.port.post.mk>

#### ufoai23/distinfo (draft)

    MD5 (ufoai/ufoai-2.3-data.tar) = 08fa6d5c80231468c4d5e886600c8dcf
    SHA256 (ufoai/ufoai-2.3-data.tar) = 0e535ce268e9a9ae08cee9b8b62ffed055bdb3182f86bf5c429ec4c54c9fa224
    SIZE (ufoai/ufoai-2.3-data.tar) = 529571840
    MD5 (ufoai/ufoai-2.3-source.tar.bz2) = 9d180ed896a58fe0e514601cd7637dc1
    SHA256 (ufoai/ufoai-2.3-source.tar.bz2) = e9c231117b779bab94bcd82c6bbf2051b2b310d7a13eb4bba10085ce0b0e64dd
    SIZE (ufoai/ufoai-2.3-source.tar.bz2) = 9839841

#### ufoai23/pkg-descr (from 2.2.1)

    UFO ALIEN INVASION is a strategy game featuring tactical combat against hostile
    alien forces which are about to infiltrate earth at this very moment. You are
    in command of a small special unit which has been founded to face the alien
    strike force. To be successful on the long run, you will also have to have a
    research team study the aliens and their technologies in order to learn as much
    as possible about their technology, their goals and the aliens themselves.

    WWW:    http://ufoai.ninex.info/

#### ufoai23/pkg-plist (draft)

    # I've not checked this plist yet, added entries for uforadiant
    bin/ufo
    %%UFOSERVER%%bin/ufoded
    %%UFO2MAP%%bin/ufo2map
    %%UFORADIANT%%bin/uforadiant
    lib/ufoai/base/game.so
    lib/ufoai/base/irc_motd.txt
    lib/ufoai/base/i18n/cs/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/da/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/de/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/el/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/en/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/es/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/es_ES/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/est/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/fi/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/fr/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/ja/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/it/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/pl/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/pt_BR/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/ru/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/slo/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/sv/LC_MESSAGES/ufoai.mo
    lib/ufoai/base/i18n/th/LC_MESSAGES/ufoai.mo
    lib/ufoai/ufo
    %%UFOSERVER%%lib/ufoai/ufoded
    %%UFO2MAP%%lib/ufoai/ufo2map
    %%UFORADIANT%%lib/ufoai/uforadiant
    lib/ufoai/base/autoexec.cfg
    lib/ufoai/base/dedicated.cfg
    lib/ufoai/base/default.cfg
    lib/ufoai/base/keys.cfg
    lib/ufoai/base/maps
    lib/ufoai/base/media
    lib/ufoai/base/models
    lib/ufoai/base/music
    lib/ufoai/base/pics
    lib/ufoai/base/shaders
    lib/ufoai/base/sound
    lib/ufoai/base/textures
    lib/ufoai/base/ufos
    @dirrm lib/ufoai/base/i18n/th/LC_MESSAGES/
    @dirrm lib/ufoai/base/i18n/th/
    @dirrm lib/ufoai/base/i18n/sv/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/sv
    @dirrm lib/ufoai/base/i18n/slo/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/slo
    @dirrm lib/ufoai/base/i18n/ru/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/ru
    @dirrm lib/ufoai/base/i18n/pt_BR/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/pt_BR
    @dirrm lib/ufoai/base/i18n/pl/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/pl
    @dirrm lib/ufoai/base/i18n/ja/LC_MESSAGES/
    @dirrm lib/ufoai/base/i18n/ja
    @dirrm lib/ufoai/base/i18n/it/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/it
    @dirrm lib/ufoai/base/i18n/fi/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/fi
    @dirrm lib/ufoai/base/i18n/fr/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/fr
    @dirrm lib/ufoai/base/i18n/est/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/est
    @dirrm lib/ufoai/base/i18n/es/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/es
    @dirrm lib/ufoai/base/i18n/es_ES/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/es_ES
    @dirrm lib/ufoai/base/i18n/en/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/en
    @dirrm lib/ufoai/base/i18n/el/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/el
    @dirrm lib/ufoai/base/i18n/de/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/de
    @dirrm lib/ufoai/base/i18n/da/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/da
    @dirrm lib/ufoai/base/i18n/cs/LC_MESSAGES
    @dirrm lib/ufoai/base/i18n/cs
    @dirrm lib/ufoai/base/i18n
    @dirrmtry lib/ufoai/base
    @dirrmtry lib/ufoai

#### ufoai23/files/pkg-message.in (draft)

    ###############################################################################

    The UFO ALien Invasion was installed

    1) Run the UFO Client using:

       # ufo

    2) or UFO Dedicated Server using:

       # ufoded

    3) or UFO Maps Tool using:

       # ufo2map

    4) or UFO Radiant using:

       # uforadiant

    5) If you are using the UFO CLient, you need a minimal 1024x968 resolution. It
       avoids some problems during the game.

    6) Enjoy it  ;)

    ###############################################################################

#### ufoai23/files/run.sh.in (from 2.2.1)

    #!/bin/sh

    cd @UFODIR@ || exit 1
    exec @UFODIR@/@APP@ "$@"

### UFO:AI 2.4 dev

BSD Licence for the portfiles, which are based upon ufoai-2.2.1 port.

#### ufoai-devel/Makefile (draft)

    # New ports collection makefile for:    ufoai-devel
    # Date created:     2010-07-30
    # Whom:         Hakisho Nukama <nukama@>
    #
    # $FreeBSD: ports/games/ufoai-devel/Makefile
    #

    PORTNAME=   ufoai-devel
    PORTVERSION=    31071
    CATEGORIES= games
    MASTER_SITES=   SF/${PORTNAME}/UFO_AI%202.x/${PORTVERSION}
    DISTNAME=   ${PORTNAME}-${PORTVERSION}
    DISTFILES=  ${PORTNAME}-${PORTVERSION}.tar.bz2
    DIST_SUBDIR=    ${PORTNAME}

    MAINTAINER= nukama@
    COMMENT=    A strategy game featuring tactical combat

    FETCH_DEPENDS=  svn:${PORTSDIR}/devel/subversion \
            rsync:${PORTSDIR}/net/rsync

    EXTRACT_DEPENDS=unzip:${PORTSDIR}/archivers/unzip

    LIB_DEPENDS=    vorbis:${PORTSDIR}/audio/libvorbis \
            jpeg.11:${PORTSDIR}/graphics/jpeg \
            png.6:${PORTSDIR}/graphics/png \
            curl:${PORTSDIR}/ftp/curl \
            theora:${PORTSDIR}/multimedia/libtheora \
            xvidcore:${PORTSDIR}/multimedia/xvid \
            gtkglext-x11:${PORTSDIR}/x11-toolkits/gtkglext

    USE_GL=     yes
    USE_SDL=    sdl mixer ttf image
    USE_OPENAL= al
    USE_GETTEXT=    yes
    GNU_CONFIGURE=  yes
    USE_GMAKE=  yes
    # UFORadiant needs these. Extra configuration without these. Without UFORadiant no tactical missions.
    USE_GNOME=  gtk20 glib20 gtksourceview2 libxml2
    CONFIGURE_ARGS+=    --enable-release=no
    # portlint warning
    CONFIGURE_ENV+=     LDFLAGS="-L${LOCALBASE}/lib ${PTHREAD_LIBS}" \
                CFLAGS="${CFLAGS} -I${LOCALBASE}/include" \
                CPPFLAGS="-I${LOCALBASE}/include ${PTHREAD_CFLAGS}"

    DATADIR=    share/${PORTNAME}
    #SUB_FILES= pkg-message
    # sourcefile extracts here:
    WRKSRC=     ${WRKDIR}/trunk
    UFO_DIR=    ${PREFIX}/lib/${PORTNAME}
    UFO_FILES=  ufo

    DESKTOP_ENTRIES=    "UFO:AI" "A squad-based tactical strategy game" \
                "${DATADIR}/ufoai.xpm" \
                "ufo" "Application;Game;StrategyGame;" \
                false \

    OPTIONS=        SVN "Fetch from subversion" on \
                SERVER  "Install dedicated server"  on \
                UFO2MAP "Install UFO tools" on \
                UFORADIANT "Install UFORADIANT mapeditor"     off \
                LANG "Compile translation"     off \
                MAPS "Compile MAPS"     off \
                MAPGET "Download MAPS"     off \
                PK3 "Assemble pk3 files"     off \

    .include <bsd.port.pre.mk>

    .if ${ARCH} == "amd64"
    CONFIGURE_TARGET?=  x86_64-portbld-freebsd${OSREL}
    #.else
    #CONFIGURE_TARGET=  ${ARCH}-portbld-freebsd${OSREL}
    .endif

    .if !defined(WITHOUT_SERVER)
    CONFIGURE_ARGS+=    --enable-dedicated
    UFO_FILES+= ufoded
    PLIST_SUB+= UFOSERVER=""
    .else
    CONFIGURE_ARGS+=    --disable-dedicated
    PLIST_SUB+= UFOSERVER="@comment "
    .endif

    .if !defined(WITHOUT_UFO2MAP)
    CONFIGURE_ARGS+=    --enable-ufo2map
    UFO_FILES+= ufo2map
    PLIST_SUB+= UFO2MAP=""
    .else
    CONFIGURE_ARGS+=    --disable-ufo2map
    PLIST_SUB+= UFO2MAP="@comment "
    .endif

    .if !defined(WITHOUT_UFORADIANT)
    CONFIGURE_ARGS+=    --enable-uforadiant
    UFO_FILES+= uforadiant
    PLIST_SUB+= UFORADIANT=""
    .else
    CONFIGURE_ARGS+=    --disable-uforadiant
    PLIST_SUB+= UFORADIANT="@comment "
    .endif

    pre-fetch:
    # make svn, if svn tree not existent.

    #Type 'make svn' to update svn source to r${PORTVERSION}
    #maybe implement use make svn 31071 to update to svn rev with svn co -r $1 ?
    svn:
    .if !defined(WITHOUT_SVN)
        svn cleanup ${DISTDIR}/${DIST_SUBDIR}/trunk/
    #SVN-Destination in distdir, shouldn't get wiped by a make clean.
        svn co -r ${PORTVERSION} https://ufoai.svn.sourceforge.net/svnroot/ufoai/ufoai/trunk ${DISTDIR}/${DIST_SUBDIR}/trunk/
    #RELEASE
    #svn co https://ufoai.svn.sourceforge.net/svnroot/ufoai/ufoai/branches/ufoai_2.3 ${DISTDIR}/ufoai-2.3/trunk
    #Create an empty tar in ${DISTDIR}/${DIST_SUBDIR} to please ports-system
        touch ${DISTDIR}/${DIST_SUBDIR}/${PORTNAME}-${PORTVERSION}.tar.bz2
        make makesum
    .endif

    pre-configure:
    .if !defined(WITHOUT_SVN)
        rsync -avP ${DISTDIR}/${DIST_SUBDIR}/trunk/* ${WRKDIR}/trunk/
        #rsync -avP ${DISTDIR}/ufoai-2.3/trunk/* ${WRKDIR}/trunk/
    .endif

    post-patch:

    pre-install:

    post-build:
    .if !defined(WITHOUT_LANG)
        @cd ${WRKSRC} && ${GMAKE} lang
    .endif
    .if !defined(WITHOUT_UFORADIANT)
        @cd ${WRKSRC} && ${GMAKE} uforadiant
    .endif
    .if !defined(WITHOUT_MAPS)
        @cd ${WRKSRC} && ${GMAKE} maps
    .endif
    .if !defined(WITHOUT_MAPGET)
        @cd ${WRKSRC} && contrib/scripts/map-get.py upgrade
    .endif
    .if !defined(WITHOUT_PK3)
        @cd ${WRKSRC} && ${GMAKE} pk3
    .endif

    do-install:

    post-install:
    #   @${CAT} ${PKGMESSAGE}

    .include <bsd.port.post.mk>

ufoai-devel/distinfo (generated for empty archive)

ufoai-devel/pkg-descr (ufoai23-version)

ufoai-devel/pkg-plist (ufoai23-version)

ufoai-devel/files/pkg-message.in (ufoai23-version)

### Problems

My build inside a fresh x86_64-jail works. But with my host system (with
old packages) I experienced a problem (undefined reference to backtrace)
while building src/ports/unix regardless of revision.

     * [UFO] src/client/battlescape/cl_battlescape.c
    src/client/battlescape/cl_battlescape.c: In function 'Grid_DumpWholeClientMap_f':
    src/client/battlescape/cl_battlescape.c:271: warning: implicit declaration of function 'RT_DumpWholeMap'
    src/client/battlescape/cl_battlescape.c: In function 'Grid_DumpClientRoutes_f':
    src/client/battlescape/cl_battlescape.c:284: warning: implicit declaration of function 'RT_WriteCSVFiles'

     * [UFO] src/server/sv_ccmds.c
    src/server/sv_ccmds.c: In function 'Grid_DumpWholeServerMap_f':
    src/server/sv_ccmds.c:583: warning: implicit declaration of function 'RT_DumpWholeMap'
    src/server/sv_ccmds.c: In function 'Grid_DumpServerRoutes_f':
    src/server/sv_ccmds.c:596: warning: implicit declaration of function 'RT_WriteCSVFiles'

     * [UFO] src/ports/unix/unix_main.c
     * [UFO] ... linking -L/usr/local/lib -pthread  (-L/usr/local/lib -lvorbis -lm -logg     -lm   -lz  -L/usr/local/lib -lcurl -rpath=/usr/lib:/usr/local/lib -lssl -lcrypto -lz -ljpeg  -L/usr/local/lib -lpng -lz -lm   -Wl,-rpath,/usr/local/lib -pthread -L/usr/local/lib -lSDL   -Wl,-rpath,/usr/local/lib -pthread -L/usr/local/lib -lSDL_image -lSDL   -Wl,-rpath,/usr/local/lib -pthread -L/usr/local/lib -lSDL_mixer -lSDL   -lSDL_ttf  -logg  -lxvidcore  -L/usr/local/lib -ltheora -logg   -lintl -lxvidcore  -lGL -Wl,-rpath,/usr/local/lib -pthread -L/usr/local/lib -lSDL  )
    debug-freebsd-x86_64/client/ports/unix/unix_main.o(.text+0xb48): In function `Sys_Backtrace':
    src/ports/unix/unix_main.c:380: undefined reference to `backtrace'
    debug-freebsd-x86_64/client/ports/unix/unix_main.o(.text+0xb5f):src/ports/unix/unix_main.c:381: undefined reference to `backtrace_symbols_fd'
    gmake: *** [ufo] Error 1

### possible upstream changes

- fix in configure.ac upstream: sysctl -n hw.machine_arch -\> amd64 -\>
  x86_64

<!-- -->

    #Makefile fix
    .if ${ARCH} == "amd64"
    CONFIGURE_TARGET?=x86_64-portbld-freebsd${OSREL}
    .endif