#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

# AC_PREREQ(2.61)
AC_INIT([freecell],[1.2.5],[tmp6154@yandex.ru])

AM_INIT_AUTOMAKE

AC_PREFIX_DEFAULT([/usr/games])

# Checks for programs.
AC_PROG_CC

# Checks for libraries.
AC_CHECK_LIB([ncurses], [start_color])
AC_SEARCH_LIBS([cbreak], [tinfo ncurses])

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADERS([stdlib.h string.h unistd.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST

# Checks for library functions.
AC_FUNC_MALLOC
AC_CHECK_FUNCS([strdup])

AC_CONFIG_FILES([Makefile src/Makefile doc/Makefile])
AC_OUTPUT
