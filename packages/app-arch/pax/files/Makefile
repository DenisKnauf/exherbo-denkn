# 2012 Denis Knauf
#	$OpenBSD: Makefile,v 1.10 2001/05/26 00:32:20 millert Exp $

# To install on versions prior to BSD 4.4 the following may have to be
# defined with CFLAGS +=
#
# -DLONG_OFF_T	Define this if the base type of an off_t is a long (and is
#		NOT a quad).  (This is often defined in the file
#		/usr/include/sys/types.h).
# 		This define is important, as if you do have a quad_t
# 		off_t and define LONG_OFF_T, pax will compile but will
# 		NOT RUN PROPERLY.
#

PROG=   pax
SRCS= 	ar.c       buf_subs.c  file_subs.c  getoldopt.c  pax.c       tar.c \
	ar_io.c    cache.c     ftree.c      options.c    sel_subs.c  tty_subs.c \
	ar_subs.c  cpio.c      gen_subs.c   pat_rep.c    tables.c

OBJS=	$(SRCS:.c=.o)
MAN=	pax.1

CFLAGS= -Wall -O2 -g\
	-DNET2_STAT -D_PATH_DEFTAPE=\"/dev/rmt0\" -DDEBIAN -D_GNU_SOURCE

prefix=/usr

pax:	$(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o $@ $(LIBS)

clean:
	$(RM) *.o

realclean: clean
	$(RM) $(PROG)

install:
	install -d $(DESTDIR)$(prefix)/bin $(DESTDIR)$(prefix)/share/man/man1
	install -s $(PROG) $(DESTDIR)$(prefix)/bin
	install    $(MAN)  $(DESTDIR)$(prefix)/share/man/man1
