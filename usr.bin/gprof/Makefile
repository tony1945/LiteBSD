#	@(#)Makefile	8.1 (Berkeley) 6/29/93

PROG=	gprof
SRCS=	gprof.c arcs.c dfn.c lookup.c ${MACHINE}.c hertz.c \
	printgprof.c printlist.c

beforeinstall:
	install -d ${DESTDIR}/usr/share/misc
	install -c -m 444 \
	    ${.CURDIR}/gprof.flat ${.CURDIR}/gprof.callg \
	    ${DESTDIR}/usr/share/misc

.include <bsd.prog.mk>
