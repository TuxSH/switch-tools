#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ(2.61)
AC_INIT([switch-tools],[1.3.0],[https://github.com/switchbrew/switch-tools/issues])
AC_CONFIG_SRCDIR([src/build_pfs0.c])

AM_INIT_AUTOMAKE([subdir-objects])

AC_CANONICAL_BUILD
AC_CANONICAL_HOST

AC_PROG_CC


PKG_CHECK_MODULES([LZ4],
		[liblz4 >= 1.7.1 liblz4 < 100],
		[have_lz4="yes"],
		[PKG_CHECK_MODULES([LZ4],
			[liblz4 >= 131],
			[have_lz4="yes"])
])

PKG_CHECK_MODULES([ZLIB], zlib, [
  AC_DEFINE([HAVE_LIBZ], [1], [Define if using zlib.])
])

NET_LIBS=""

case "$host" in
   *-*-mingw*)
      NET_LIBS="-lws2_32"
      CFLAGS="$CFLAGS -D__USE_MINGW_ANSI_STDIO"
      ;;
esac

CFLAGS="$CFLAGS -std=gnu99"

AC_SUBST(ZLIB_LIBS)
AC_SUBST(NET_LIBS)
AC_SUBST(ZLIB_CFLAGS)
AC_SUBST(LZ4_LIBS)
AC_CONFIG_FILES([Makefile])
AC_OUTPUT
