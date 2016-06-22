#  Copyright 2015, 2016, Cumulus Networks, Inc.
#  Author: Dave Olson <olson@cumulusnetworks.com>

EXTRA_DIST = ChangeLog README

lib_LTLIBRARIES = libsimple_tacacct.la
ACLOCAL_AMFLAGS = -I config

# install header file into same directory as tacplus_map
libsimple_incdir = $(includedir)/tacplus
libsimple_tacacct_la_SOURCES = simple_tacacct.c
libsimple_inc_HEADERS = tacplus/simple_tacacct.h

libsimple_tacacct_la_CFLAGS = $(AM_CFLAGS)
libsimple_tacacct_la_LDFLAGS = -version-info 1:0:0 -shared -Wl,--no-undefined
libsimple_tacacct_la_LIBADD = -laudit -ltacplus_map -ltac

# This is a test program, not to be installed or built by default.
# Use 'make check' to build it.
acct_test_SOURCES = acct_test.c
acct_test_CFLAGS = $(AM_CFLAGS)
acct_test_LDADD = -ldl -lsimple_tacacct
check_PROGRAMS = acct_test

clean-generic:
	rm -rf autom4te*.cache 
	rm -f *.rej *.orig *.lang

MAINTAINERCLEANFILES = Makefile.in config.h.in configure aclocal.m4 \
                       config/config.guess  config/config.sub  config/depcomp \
                       config/install-sh config/ltmain.sh config/missing

striplib = $(STRIP)--keep-symbol=send_tacacs_acct

#install-data-hook:
#	${INSTALL} -d $(DESTDIR)$(libdir)/
#	${INSTALL} -m 755 audisp-tacplus $(DESTDIR)$(sbindir)
#	$(STRIP) --keep-symbol=send_tacacs_acct $(DESTDIR)$(libdir)/$(NSS_TACPLUS_LIBC_VERSIONED)
