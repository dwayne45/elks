BASEDIR=..

include $(BASEDIR)/Make.defs

###############################################################################
#
# Include standard packaging commands.

include $(BASEDIR)/Make.rules

HOSTCC = gcc
HOST_CFLAGS = -O2

###############################################################################

#TODO: fix compress uncompress zcat lpfilter disabled
PRGS = tar miniterm ed od hd time kilo tty uuencode uudecode

#PRGS_HOST=compress.host

all: $(PRGS) $(PRGS_HOST)

ed: ed.o
	$(LD) $(LDFLAGS) -o ed ed.o $(LDLIBS)

tar: tar.o
	$(LD) $(LDFLAGS) -o tar tar.o $(LDLIBS)
	
od: od.o
	$(LD) $(LDFLAGS) -o od od.o $(LDLIBS)

hd: hd.o
	$(LD) $(LDFLAGS) -o hd hd.o $(LDLIBS)

time: time.o
	$(LD) $(LDFLAGS) -o time time.o $(LDLIBS)

kilo: kilo.o
	$(LD) $(LDFLAGS) -maout-heap=0xffff -o kilo kilo.o $(LDLIBS)

tty: tty.o
	$(LD) $(LDFLAGS) -o tty tty.o $(LDLIBS)

compress: compress.o
	$(LD) $(LDFLAGS) -o compress compress.o $(LDLIBS)

miniterm: miniterm.o
	$(LD) $(LDFLAGS) -o miniterm miniterm.o $(LDLIBS)

uuencode: uuencode.o
	$(LD) $(LDFLAGS) -o uuencode uuencode.o $(LDLIBS)

uudecode: uudecode.o
	$(LD) $(LDFLAGS) -o uudecode uudecode.o $(LDLIBS)

compress.host: compress.c
	$(HOSTCC) $(HOST_CFLAGS) -s compress.c -o $@

uncompress: compress
	ln -sf compress uncompress

zcat: compress
	ln -sf compress zcat

install: $(PRGS)
	$(INSTALL) $(PRGS) $(DESTDIR)/bin

clean:
	rm -f $(PRGS) $(PRGS_HOST) *~ *.o
