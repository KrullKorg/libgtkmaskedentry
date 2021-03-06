AC_PREREQ(2.59)
AC_INIT([GtkMaskedEntry], [0.0.4], [azagli@libero.it])
AC_CONFIG_SRCDIR([src/gtkmaskedentry.c])
AM_CONFIG_HEADER(config.h)

AM_INIT_AUTOMAKE(AC_PACKAGE_NAME, AC_PACKAGE_VERSION, -Wall)

m4_ifdef([AM_SILENT_RULES],[AM_SILENT_RULES([yes])])

AM_MAINTAINER_MODE

AC_LIBTOOL_WIN32_DLL

AC_PROG_CXX
AC_PROG_CC
AC_PROG_CPP
AC_PROG_INSTALL
AC_PROG_LN_S
AC_PROG_MAKE_SET
AC_PROG_LIBTOOL

AC_CANONICAL_SYSTEM

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADERS([string.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST

GTK_DOC_CHECK(1.0)

PKG_CHECK_MODULES(GTK, gtk+-3.0 >= 3.0.0)
PKG_CHECK_EXISTS(gladeui-2.0 >= 3.10.0, [GLADEUI_FOUND=yes], [GLADEUI_FOUND=no])
PKG_CHECK_EXISTS(libgtkform >= 0.5.0, [LIBGTKFORM_FOUND=yes], [LIBGTKFORM_FOUND=no])

AC_SUBST(GTK_CFLAGS)
AC_SUBST(GTK_LIBS)

AM_CONDITIONAL(GLADEUI_FOUND, test $GLADEUI_FOUND = yes)
AM_CONDITIONAL(LIBGTKFORM_FOUND, test $LIBGTKFORM_FOUND = yes)

if test $LIBGTKFORM_FOUND = yes; then
PKG_CHECK_MODULES(GTKFORM, libgtkform >= 0.5.0)

AC_SUBST(GTKFORM_CFLAGS)
AC_SUBST(GTKFORM_LIBS)
fi

dnl ******************************
dnl Check for Operating System
dnl ******************************

platform_win32=no

case "$host" in
*-mingw*)
    platform_win32=yes
    ;;
esac

AM_CONDITIONAL(PLATFORM_WIN32, [test $platform_win32 = yes])

# Output files
AC_CONFIG_FILES([
  libgtkmaskedentry.pc
  Makefile 
  src/Makefile
  tests/Makefile
  docs/Makefile
  docs/reference/Makefile
  docs/reference/version.xml
])

if test $GLADEUI_FOUND = yes; then
AC_CONFIG_FILES([
  glade/Makefile
  glade/icons/Makefile
  glade/icons/hicolor/Makefile
  glade/icons/hicolor/16x16/Makefile
  glade/icons/hicolor/16x16/actions/Makefile
  glade/icons/hicolor/22x22/Makefile
  glade/icons/hicolor/22x22/actions/Makefile
])
fi

AC_OUTPUT
