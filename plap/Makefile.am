#  OpenVPN-PLAP-Provider
#
#  Copyright (C) 2021-2022 Selva Nair <selva.nair@gmail.com>
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program (see the file COPYING included with this
#  distribution); if not, write to the Free Software Foundation, Inc.,
#  59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

RCCOMPILE = $(WINDRES) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) \
	$(AM_CPPFLAGS) $(CPPFLAGS)
LTRCCOMPILE = $(LIBTOOL) --mode=compile --tag=RC $(RCCOMPILE)

.rc.lo:
	$(LTRCCOMPILE) -i "$<" -o "$@"

.rc.o:
	$(RCCOMPILE) -i "$<" -o "$@"

MAINTAINERCLEANFILES = \
	$(srcdir)/Makefile.in

lib_LTLIBRARIES = libopenvpn_plap.la

libopenvpn_plap_la_CFLAGS = -DDISABLE_PASSWORD_CHANGE -D_UNICODE -municode

libopenvpn_plap_la_RESOURCES = \
	$(top_srcdir)/res/openvpn-gui-res-cs.rc \
	$(top_srcdir)/res/openvpn-gui-res-de.rc \
	$(top_srcdir)/res/openvpn-gui-res-dk.rc \
	$(top_srcdir)/res/openvpn-gui-res-en.rc \
	$(top_srcdir)/res/openvpn-gui-res-es.rc \
	$(top_srcdir)/res/openvpn-gui-res-fa.rc \
	$(top_srcdir)/res/openvpn-gui-res-fi.rc \
	$(top_srcdir)/res/openvpn-gui-res-fr.rc \
	$(top_srcdir)/res/openvpn-gui-res-it.rc \
	$(top_srcdir)/res/openvpn-gui-res-jp.rc \
	$(top_srcdir)/res/openvpn-gui-res-kr.rc \
	$(top_srcdir)/res/openvpn-gui-res-nl.rc \
	$(top_srcdir)/res/openvpn-gui-res-no.rc \
	$(top_srcdir)/res/openvpn-gui-res-pl.rc \
	$(top_srcdir)/res/openvpn-gui-res-pt.rc \
	$(top_srcdir)/res/openvpn-gui-res-ru.rc \
	$(top_srcdir)/res/openvpn-gui-res-se.rc \
	$(top_srcdir)/res/openvpn-gui-res-tr.rc \
	$(top_srcdir)/res/openvpn-gui-res-ua.rc \
	$(top_srcdir)/res/openvpn-gui-res-zh-hans.rc \
	$(top_srcdir)/res/openvpn-gui-res-zh-hant.rc \
	$(top_srcdir)/res/connected.ico \
	$(top_srcdir)/res/connecting.ico \
	$(top_srcdir)/res/disconnected.ico \
	$(top_srcdir)/res/openvpn-gui.ico \
	$(top_srcdir)/res/reconnecting.ico \
        openvpn-plap-res.rc \
	openvpn-plap.manifest

openvpn-plap-res.lo: $(libopenvpn_plap_la_RESOURCES) $(top_srcdir)/openvpn-gui-res.h
EXTRA_DIST = openvpn-plap-res.rc openvpn-plap.manifest

libopenvpn_plap_la_SOURCES = \
	stub.c plap_provider.c \
	plap_connection.h plap_connection.c \
	plap_common.h plap_common.c \
	plap_dll.h plap_dll.c \
	ui_glue.h ui_glue.c \
	$(top_srcdir)/openvpn.c \
	$(top_srcdir)/localization.c\
	$(top_srcdir)/options.c \
	$(top_srcdir)/proxy.c \
	$(top_srcdir)/registry.c \
	$(top_srcdir)/manage.c \
	$(top_srcdir)/misc.c \
	$(top_srcdir)/openvpn_config.c \
	$(top_srcdir)/config_parser.c \
	$(top_srcdir)/pkcs11.c \
	openvpn-plap-res.rc

libopenvpn_plap_la_LIBADD = \
	-lws2_32 \
	-lcomctl32 \
	-lwinhttp \
	-lcrypt32 \
	-lole32 \
	-lshlwapi \
	-lgdi32 \
	-lrpcrt4

libopenvpn_plap_la_LDFLAGS = -no-undefined -avoid-version -static-libgcc