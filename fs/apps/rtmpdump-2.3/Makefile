#$L$
# Copyright (C) 2011 Ridgerun (http://www.ridgerun.com). 
##$L$

PKG_URL=http://rtmpdump.mplayerhq.hu/download/
PKG_TARBALL=rtmpdump-2.3.tgz
PKG_SHA1SUM=b65ce7708ae79adb51d1f43dd0b6d987076d7c42

export LDFLAGS=-Wl,--rpath-link -Wl,$(FSDEVROOT)/usr/lib

BINARIES= /usr/bin/rtmpdump \
          /usr/sbin/{rtmpgw,rtmpsrv,rtmpsuck}
LIBRARIES= /usr/lib/librtmp.so.0
CORRECT_PKGCONFIG=/usr/lib/pkgconfig/librtmp.pc

CCACHE_ENABLE=no

APPS_CFLAGS+=-I$(FSDEVROOT)/usr/include
FETCHER_EXTRACT_DIRECTORY_NAME=src
build: rrfetched built

installed:
	$(MAKE) -C src SYS=posix prefix=/usr DESTDIR=$(FSDEVROOT) install $(QOUT)

install: installed rrsdk_install

clean:
	$(V) rm -Rf installed built

distclean: clean rrfetched_clean

include ../../../bsp/classes/rrsdk.class
include $(CLASSES)/fetcher.defs

built: 
	$(MAKE) -C src CC="$(CC)" SYS=posix prefix=/usr XCFLAGS="$(APPS_CFLAGS)" XLDFLAGS+="$(APPS_LDFLAGS)" $(QOUT)

