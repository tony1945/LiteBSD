#	@(#)Makefile	8.1 (Berkeley) 5/31/93

PROG=	phantasia
SRCS=	main.c fight.c io.c interplayer.c gamesupport.c misc.c phantglobs.c
DPADD=	${LIBM} ${LIBOCURSES} ${LIBTERM} ${LIBCOMPAT}
LDADD=	-lm -locurses -ltermlib -lcompat
HIDEGAME=hidegame
MAN6=	phantasia.0
CLEANFILES+=map setup setup.o
CFLAGS+=-DOLD_CURSES

all: setup phantasia ${MAN6}

setup: phantglobs.o setup.o monsters.asc ${LIBM} 
	${CC} phantglobs.o setup.o -o ${.TARGET} -lm

beforeinstall: 
	./setup -m ${.CURDIR}/monsters.asc
	chown games.bin /var/games/phantasia/*

# Make Phantasia map.  Change the map commands reflect your installation.
# PLOTDEVICE is used for plotting the map.  Change as appropriate.

map: map.c
	${CC} -O ${.CURDIR}/map.c -lplot -o ${.TARGET}
	./map | plot > /dev/tty

phantasia.0: phantasia.6
	tbl ${.CURDIR}/phantasia.6 | nroff -man > ${.TARGET}

.include <bsd.prog.mk>
