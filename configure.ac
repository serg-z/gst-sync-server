AC_INIT([gst-sync-server], [0.0.1])
AC_CONFIG_SRCDIR([Makefile.am])
AC_CONFIG_HEADERS(config.h)

dnl Add parameters for aclocal (keep in sync with Makefile.am)
AC_SUBST(ACLOCAL_AMFLAGS, "-I m4 -I common/m4")
AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE([-Wno-portability 1.11 no-dist-gzip dist-xz tar-ustar subdir-objects])
AM_MAINTAINER_MODE

LT_PREREQ([2.2.6])
LT_INIT([dlopen win32-dll pic-only])

m4_ifdef([AM_SILENT_RULES],
  [AM_SILENT_RULES([yes])],
  [
    AM_DEFAULT_VERBOSITY=1
    AC_SUBST(AM_DEFAULT_VERBOSITY)
  ]
)

AC_PROG_CC
AC_PROG_CC_STDC
AC_PROG_INSTALL
AM_PROG_CC_C_O

AC_HEADER_STDC
AC_C_CONST
AC_ISC_POSIX

PKG_PROG_PKG_CONFIG

PKG_CHECK_MODULES(GLIB, [glib-2.0 gobject-2.0 gio-2.0 > 2.44 ])
PKG_CHECK_MODULES(JSON_GLIB, [json-glib-1.0 >= 1.2])
PKG_CHECK_MODULES(GST, [gstreamer-1.0 gstreamer-net-1.0 >= 1.6])

GST_API_VERSION=1.0
AC_SUBST(GST_API_VERSION)

WARNING_CFLAGS="-Wall"
AC_SUBST(WARNING_CFLAGS)

dnl check for documentation tools
AG_GST_DOCBOOK_CHECK
GTK_DOC_CHECK([1.12])

AC_CONFIG_FILES([
  Makefile
  common/Makefile
  common/m4/Makefile
  gst-libs/Makefile
  gst-libs/gst/Makefile
  gst-libs/gst/sync-server/Makefile
  docs/Makefile
  docs/version.entities
  docs/libs/Makefile
  examples/Makefile
])

AC_OUTPUT
