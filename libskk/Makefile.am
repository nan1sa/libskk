lib_LTLIBRARIES = libskk.la

libskk_la_VALAFLAGS = \
	-H libskk.h --vapi skk-@SKK_API_VERSION@.vapi \
	-h skk-internals.h \
	--vapidir=. \
	--pkg glib-2.0 --pkg gio-2.0 --pkg gee-1.0 --pkg posix \
	--internal-vapi skk-internals-@SKK_API_VERSION@.vapi \
	--library skk-@SKK_API_VERSION@ --gir Skk-@SKK_API_VERSION@.gir \
	$(VALAFLAGS)

libskk_la_CFLAGS = \
	$(LIBSKK_CFLAGS)
libskk_la_LIBADD = \
	$(LIBSKK_LIBS)

libskkincludedir = $(includedir)/libskk

skkinclude_headers = \
	libskk.h

libskkinclude_HEADERS = \
	$(skk_headers)

libskk_la_SOURCES = \
	rom-kana.vala \
	converter.vala \
	dict.vala \
	file-dict.vala \
	state.vala \
	context.vala

if HAVE_INTROSPECTION
girdir = $(datadir)/gir-1.0
gir_DATA = Skk-@SKK_API_VERSION@.gir

typelibdir = $(libdir)/girepository-1.0
typelib_DATA = Skk-@SKK_API_VERSION@.typelib

Skk-@SKK_API_VERSION@.typelib: Skk-@SKK_API_VERSION@.gir
	@INTROSPECTION_COMPILER@ --shared-library=libskk -o $@ $^
endif

Skk-@SKK_API_VERSION@.gir skk-internals-@SKK_API_VERSION@.vapi skk-@SKK_API_VERSION@.vapi: libskk.la

CLEANFILES = \
	skk-@SKK_API_VERSION@.vapi \
	skk-internals-@SKK_API_VERSION@.vapi \
	Skk-@SKK_API_VERSION@.typelib \
	Skk-@SKK_API_VERSION@.gir \
	*.[ch]