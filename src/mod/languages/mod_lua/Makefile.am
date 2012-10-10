VERBOSE=1
include $(top_srcdir)/build/modmake.rulesam

MODNAME=mod_lua

AM_CFLAGS += $(CFLAGS) -D_GNU_SOURCE
mod_LTLIBRARIES = mod_lua.la
mod_lua_la_SOURCES = mod_lua.cpp freeswitch_lua.cpp mod_lua_wrap.cpp
mod_lua_la_CXXFLAGS = `pkg-config --cflags lua5.1` $(AM_CPPFLAGS)
mod_lua_la_LIBADD = $(switch_builddir)/libfreeswitch.la 
mod_lua_la_LDFLAGS = -avoid-version -module -no-undefined -shared -lm -ldl $(AM_LDFLAGS) `pkg-config --libs lua5.1` $(SOLINK)

reswig: swigclean lua_wrap

allclean: clean

swigclean: clean
	rm -f mod_lua_wrap.*

lua_wrap: mod_lua_extra.c
	swig -lua -c++ -I../../../../src/include -oh mod_lua_wrap.h -o mod_lua_wrap.cpp freeswitch.i
	echo "#include \"mod_lua_extra.c\"" >> mod_lua_wrap.cpp
	patch -s -p0 -i hack.diff

