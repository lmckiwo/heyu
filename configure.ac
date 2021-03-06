#
# configure.ac - Autoconf source file for Heyu
#
# Copyright (C) 2011, 2012, 2015 Janusz Krzysztofik <jkrzyszt@tis.icnet.pl>
#
# Derived from an initial version genereted automatically by the
# autoscan application.
#
#   This program is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])
AC_INIT([Heyu], [2.11-rc2],
	[heyu@tickets.assembla.com], [heyu], [http://heyu.org])
AC_DEFINE([RELEASE_DATE], ["20150320"], [Release date of package])
AC_COPYRIGHT([Heyu specific bits:
Copyright (C) 2011, 2012, 2015 Janusz Krzysztofik <jkrzyszt@tis.icnet.pl>])
AC_CONFIG_SRCDIR([relay.c])
AC_CONFIG_HEADERS([config.h])

# Optional Features
AC_MSG_CHECKING([whether to enable CM17A Firecracker support])
	AC_ARG_ENABLE([cm17a], [AS_HELP_STRING([--disable-cm17a],
		[omit support for optional CM17A Firecracker device])], [],
		[enable_cm17a=yes])
	AC_MSG_RESULT([$enable_cm17a])
	AS_IF([test "x$enable_cm17a" != "xno"], [AC_DEFINE([HAVE_FEATURE_CM17A],
		[1], [Define if you have the CM17A Firecracker device])], [])
AC_MSG_CHECKING([whether to enable extended type 0 shutter controllers support])
	AC_ARG_ENABLE([ext0], [AS_HELP_STRING([--disable-ext0],
		[omit support for extended type 0 shutter controllers])], [],
		[enable_ext0=yes])
	AC_MSG_RESULT([$enable_ext0])
	AS_IF([test "x$enable_ext0" != "xno"], [AC_DEFINE([HAVE_FEATURE_EXT0],
		[1], [Define if you have extended type 0 shutter controllers])],
		[])
AC_MSG_CHECKING([whether to enable RFXSensors support])
	AC_ARG_ENABLE([rfxs], [AS_HELP_STRING([--disable-rfxs],
		[omit support for RFXSensors])], [], [enable_rfxs=yes])
	AC_MSG_RESULT([$enable_rfxs])
	AS_IF([test "x$enable_rfxs" != "xno"], [AC_DEFINE([HAVE_FEATURE_RFXS],
		[1], [Define if you have RFXSensors])], [])
AC_MSG_CHECKING([whether to enable RFXMeters support])
	AC_ARG_ENABLE([rfxm], [AS_HELP_STRING([--disable-rfxm],
		[omit support for RFXMeters])], [], [enable_rfxm=yes])
	AC_MSG_RESULT([$enable_rfxm])
	AS_IF([test "x$enable_rfxm" != "xno"], [AC_DEFINE([HAVE_FEATURE_RFXM],
		[1], [Define if you have RFXMeters])], [])
AC_MSG_CHECKING([whether to enable Digimax thermostat support])
	AC_ARG_ENABLE([dmx], [AS_HELP_STRING([--disable-dmx],
		[omit support for the Digimax thermostat])], [],
		[enable_dmx=yes])
	AC_MSG_RESULT([$enable_dmx])
	AS_IF([test "x$enable_dmx" != "xno"], [AC_DEFINE([HAVE_FEATURE_DMX],
		[1], [Define if you have Digimax thermostats])], [])
AC_MSG_CHECKING([whether to enable Oregon sensors support])
	AC_ARG_ENABLE([ore], [AS_HELP_STRING([--disable-ore],
		[omit support for Oregon sensors])], [], [enable_ore=yes])
	AC_MSG_RESULT([$enable_ore])
	AS_IF([test "x$enable_ore" != "xno"], [AC_DEFINE([HAVE_FEATURE_ORE],
		[1], [Define if you have Oregon sensors])], [])
AC_MSG_CHECKING([whether to enable support for KaKu/HomeEasy signals])
	AC_ARG_ENABLE([kaku], [AS_HELP_STRING([--disable-kaku],
		[omit support for KaKu/HomeEasy signals])], [],
		[enable_kaku=yes])
	AC_MSG_RESULT([$enable_kaku])
	AS_IF([test "x$enable_kaku" != "xno"], [AC_DEFINE([HAVE_FEATURE_KAKU],
		[1], [Define if you have KaKu/HomeEasy devices])], [])

AC_MSG_CHECKING([whether to enable split processing of RFXCOM master/slave])
	AC_ARG_ENABLE([rfxdual], [AS_HELP_STRING([--enable-rfxdual],
		[enable independent processing of RF streams in RFXCOM dual (master/slave) receiver configurations (EXPERIMENTAL)]
		)], [], [enable_rfxdual=no])
	AC_MSG_RESULT([$enable_rfxdual])
	AS_IF([test "x$enable_rfxdual" == "xyes"], [AC_DEFINE([RFXCOM_DUAL],
		[1],
		[Define if you have a dual RFXCOM receiver and want to try an experimetal feature of independent master/slave processing]
		)], [])

AC_MSG_CHECKING([for number of user flags])
	AC_ARG_VAR([FLAGS], [set number of user flags (1 < n < 1024) [32]])
	AS_IF([test "x$FLAGS" = "x"], [FLAGS=32],
	AS_IF([test $FLAGS -ge 1 && test $FLAGS -le 1024],
		[FLAGS=`expr \( $FLAGS + 31 \) / 32 \* 32`
		AC_DEFINE_UNQUOTED([NUM_FLAG_BANKS], [`expr $FLAGS / 32`],
		[Define if you need more than 1 bank of 32 user flags each])],
		AC_MSG_FAILURE(
			[wrong FLAGS value "$FLAGS" (shoud be 1 < n < 1024)])))
	AC_MSG_RESULT([$FLAGS])
AC_MSG_CHECKING([for number of user counters])
	AC_ARG_VAR([COUNTERS],
		[set number of user counters (1 < n < 1024) [32]])
	AS_IF([test "x$COUNTERS" = "x"], [COUNTERS=32],
	AS_IF([test $COUNTERS -ge 1 && test $COUNTERS -le 1024],
		[COUNTERS=`expr \( $COUNTERS + 31 \) / 32 \* 32`
		AC_DEFINE_UNQUOTED([NUM_COUNTER_BANKS], [`expr $COUNTERS / 32`],
		[Define if you need more than 1 bank of 32 user counters each]
		)], AC_MSG_FAILURE(
		[wrong COUNTERS value "$COUNTERS" (shoud be 1 < n < 1024)])))
	AC_MSG_RESULT([$COUNTERS])
AC_MSG_CHECKING([for number of user timers])
	AC_ARG_VAR([TIMERS], [set number of user timers (1 < n < 1024) [32]])
	AS_IF([test "x$TIMERS" = "x"], [TIMERS=32],
	AS_IF([test $TIMERS -ge 1 && test $TIMERS -le 1024],
		[TIMERS=`expr \( $TIMERS + 31 \) / 32 \* 32`
		AC_DEFINE_UNQUOTED([NUM_TIMER_BANKS], [`expr $TIMERS / 32`],
		[Define if you need more than 1 bank of 32 user timers each])],
		AC_MSG_FAILURE(
		[wrong TIMERS value "$TIMERS" (shoud be 1 < n < 1024)])))
	AC_MSG_RESULT([$TIMERS])

AC_SUBST([PACKAGE], [$PACKAGE_TARNAME])
AS_CASE([$sysconfdir],
	[*$PACKAGE*], [pkgsysconfdir='$(sysconfdir)'],
	[\$\(prefix\)*|\$\{prefix\}*],
		AS_CASE([$prefix],
			[*$PACKAGE*], [pkgsysconfdir='$(sysconfdir)'],
			[pkgsysconfdir='$(sysconfdir)/$(PACKAGE)']),
	[pkgsysconfdir='$(sysconfdir)/$(PACKAGE)'])
	AC_SUBST([pkgsysconfdir], [])
AS_CASE([$CPPFLAGS],
	[*-DSYSBASEDIR=*], [],
	[CPPFLAGS=$CPPFLAGS' -DSYSBASEDIR=\"$(pkgsysconfdir)\"'])
AS_CASE([$CPPFLAGS],
	[*-DLOCKDIR=*], [],
	[CPPFLAGS=$CPPFLAGS' -DLOCKDIR=\"$(localstatedir)/lock\"'])
AS_CASE([$CPPFLAGS],
	[*-DSPOOLDIR=*], [],
	[CPPFLAGS=$CPPFLAGS' -DSPOOLDIR=\"$(localstatedir)/tmp/$(PACKAGE)\"'])

AC_MSG_CHECKING([for a custom man1dir])
	AS_IF([test "x$man1dir" != "x"], [AM_SUBST_NOTMAKE([MAN1DIR])
		AC_SUBST([MAN1DIR], [man1dir=$man1dir])], [])
	AC_MSG_RESULT([$man1dir])
AC_MSG_CHECKING([for a custom man5dir])
	AS_IF([test "x$man5dir" != "x"], [AM_SUBST_NOTMAKE([MAN5DIR])
		AC_SUBST([MAN5DIR], [man5dir=$man5dir])], [])
	AC_MSG_RESULT([$man5dir])

AC_MSG_CHECKING([for a custom post-install script])
	AC_ARG_ENABLE([postinst], AS_HELP_STRING([--enable-postinst],
	[enable custom make rules, used for calling Heyu custom post-install script]
		), AS_CASE([$enable_postinst],
			[no], [enable_postinst=],
			[yes], [enable_postinst='$(srcdir)/post-install.sh'],
			[]), [])
	AS_IF([test "x$enable_postinst" != "x"], [AM_SUBST_NOTMAKE([POSTINST])
		AC_SUBST([POSTINST], [$enable_postinst])], [])
	AM_CONDITIONAL([POSTINST], [test "x$enable_postinst" != "x"])
	AC_MSG_RESULT([$enable_postinst])

AM_INIT_AUTOMAKE([-Wall -Werror foreign])

AC_CANONICAL_HOST
AS_CASE([$host_os],
    [sco*],
	AC_DEFINE(SCO, 1, [required for correct termio handling]),
    [])

# Checks for programs.
AS_IF([test "x$CFLAGS" = "x"], [no_CFLAGS="yes"], [])
AC_PROG_CC
AS_IF([test "x$no_CFLAGS" = "xyes" && test "x$GCC" = "xyes"],
	[CFLAGS="$CFLAGS -Wall"], [])
AC_PROG_INSTALL
AC_PROG_MAKE_SET

# Checks for compiler characteristics
AC_C_INLINE

# Checks for libraries.
AC_SEARCH_LIBS([sqrt], [m])
AC_SEARCH_LIBS([nanosleep], [rt])
AC_SEARCH_LIBS([syslog], [socket])
AC_SEARCH_LIBS([tcgetattr], [posix])

# Checks for header files.
AC_CHECK_HEADERS([fcntl.h limits.h netdb.h sgtty.h stdlib.h string.h strings.h])
AC_CHECK_HEADERS([sys/filsys.h sys/ioctl.h sys/param.h sys/socket.h sys/time.h])
AC_CHECK_HEADERS([syslog.h termio.h termios.h unistd.h])
AC_CHECK_HEADERS([asm/ioctls.h errno.h linux/serial.h linux/serial_reg.h pty.h])
AC_CHECK_HEADERS([sys/errno.h sys/resource.h sys/termio.h sys/termios.h])
AC_HEADER_SYS_WAIT
AC_HEADER_TIME

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_UID_T
AC_TYPE_MODE_T
AC_TYPE_OFF_T
AC_TYPE_PID_T
AC_TYPE_UNSIGNED_LONG_LONG_INT
AC_CHECK_TYPES([void], [], [], [])
AC_CHECK_TYPES([struct termios], [], [], [
#ifdef HAVE_SYS_TERMIOS_H
# include <sys/termios.h>
#endif
#ifdef HAVE_TERMIOS_H
# include <termios.h>
#endif
])
AC_CHECK_TYPES([struct termio], [], [], [
#ifdef HAVE_SYS_TERMIO_H
# include <sys/termio.h>
#endif
#ifdef HAVE_TERMIO_H
# include <termio.h>
#endif
])

# Checks for declarations.
AC_CHECK_DECLS(timezone, [], [], [
#ifdef TIME_WITH_SYS_TIME
# include <sys/time.h>
# include <time.h>
#else
# ifdef HAVE_SYS_TIME_H
#  include <sys/time.h>
# else
#  include <time.h>
# endif
#endif
])

# Checks for library functions.
AC_FUNC_ERROR_AT_LINE
AC_FUNC_FORK
AC_FUNC_GETGROUPS
AC_FUNC_MKTIME
AC_FUNC_STRTOD
AC_CHECK_FUNCS([alarm floor ftruncate gettimeofday memmove memset putenv])
AC_CHECK_FUNCS([socket sqrt strchr strdup strerror strrchr strstr strtol])
AC_CHECK_FUNCS([nanosleep nsleep setitimer sigaction siginterrupt])
AC_CHECK_FUNCS([malloc realloc])

AC_MSG_CHECKING(whether to enable RFXLAN receiver support)
	AC_ARG_ENABLE([rfxlan], [AS_HELP_STRING([--disable-rfxlan],
		[omit support for RFXLAN receiver])], [], [enable_rfxlan=yes])
	AS_IF([test "x$enable_rfxlan" != "xno" &&
		test "x$ac_cv_header_netdb_h" != "xyes" \
			-o "x$ac_cv_func_memset" != "xyes" \
			-o "x$ac_cv_func_socket" != "xyes"],
		[enable_rfxlan=no], [])
	AC_MSG_RESULT($enable_rfxlan)
	AS_IF([test "x$enable_rfxlan" != "xno"],
		[AC_DEFINE([HAVE_FEATURE_RFXLAN], [1],
		[Define if you have RFXLAN receiver])], [])

# xPL checks and setup
AC_MSG_CHECKING([whether to build with xPL support library])
	AC_ARG_WITH([xpl], [AS_HELP_STRING([--with-xpl],
		       [build with xPL support; ARG may point to a location]
		       [where xPLLib sources can be found])], [], [with_xpl=no])
AS_IF([test "x$with_xpl" = xno], [AC_MSG_RESULT([$with_xpl])], [
	AC_MSG_RESULT([yes])
	AC_CHECK_HEADERS([xPL.h], [AC_CHECK_LIB([xPL], [xPL_initialize])])])
AS_IF([test "x$with_xpl" != xno -a "x$ac_cv_lib_xPL_xPL_initialize" != xyes], [
	AC_MSG_CHECKING([for a location to build xPLLib from])
	AS_IF([test "x$with_xpl" = xyes], [
		AC_MSG_RESULT([not specified])
		AC_MSG_FAILURE([Please specify xPLLib location to be used])
	], [	AC_MSG_RESULT([$with_xpl])
		AC_MSG_CHECKING(
			 [whether $with_xpl looks like a valid xPLLib location])
		AS_CASE([$with_xpl],
		[http://*|ftp://*], [
			AC_MSG_RESULT([yes])
			AC_SUBST([xPLLib_URL], [$with_xpl])],
		[
			read xPLLib <<EOF
$with_xpl
EOF
			AS_IF([test -f "$xPLLib" -o -f "$srcdir/$xPLLib"], [
				AC_MSG_RESULT([yes])
				AC_SUBST([xPLLib_archive], [$with_xpl])
			], [
				AS_IF([test -d "$xPLLib" \
						-o -d "$srcdir/$xPLLib"], [
					AC_MSG_RESULT([yes])
					AC_SUBST([xPLLib_srcdir], [$with_xpl])
				], [
					AC_MSG_RESULT([no])
					AC_MSG_FAILURE(
					[Please provide a valid xPLLib location]
					)])
				AS_IF([test -d "$srcdir/$xPLLib"], [
					AC_SUBST([xPL_isrc],
						  [-I$srcdir/$with_xpl])])])])])
	AS_IF([test "x$xPLLib_srcdir" = x], [
		AC_SUBST([xPLLib_srcdir], [xPLLib])
		AS_IF([test "x$xPLLib_archive" = x], [
			AC_SUBST([xPLLib_archive], [xPLLib.tgz])])])
	AS_IF([test "x$xPLLib_URL" != x], [
		AC_CHECK_PROG([WGET_O], [wget], [wget -O])
		AS_IF([test "x$WGET_O" = x], [
			AC_CHECK_PROG([WGET_O], [curl], [curl -o])])
		AS_IF([test "x$WGET_O" = x], [
			AC_MSG_FAILURE(
				[wget missing, please provide local xPLLib copy]
			)])])
	AC_PROG_RANLIB
	AS_IF([test "x$ac_cv_header_fcntl_h" = xyes -a \
			"x$ac_cv_header_netdb_h" = xyes -a \
			"x$ac_cv_header_stdlib_h" = xyes -a \
			"x$ac_cv_header_string_h" = xyes -a \
			"x$ac_cv_header_sys_ioctl_h" = xyes -a \
			"x$ac_cv_header_sys_socket_h" = xyes -a \
			"x$ac_cv_header_sys_time_h" = xyes -a \
			"x$ac_cv_header_termios_h" = xyes -a \
			"x$ac_cv_header_unistd_h" = xyes -a \
			"x$ac_cv_func_malloc_0_nonnull" = xyes -a \
			"x$ac_cv_func_realloc_0_nonnull" = xyes -a \
			"x$ac_cv_func_gettimeofday" = xyes -a \
			"x$ac_cv_func_socket" = xyes -a \
			"x$ac_cv_func_strerror" = xyes -a \
			"x$ac_cv_func_strstr" = xyes -a \
			"x$ac_cv_func_strtol" = xyes -a \
			"x$ac_cv_type_pid_t" = xyes], [
			AC_CHECK_HEADER([arpa/inet.h], [
			AC_CHECK_HEADER([netinet/in.h], [
			AC_CHECK_FUNC([bzero], [
			AC_CHECK_FUNC([inet_ntoa], [
			AC_CHECK_TYPE([uint32_t], [
		AC_MSG_NOTICE([will try to build libxPL.a from $with_xpl])
		AC_DEFINE([HAVE_XPL_H], [1],
			     [Define to 1 if you have the <xPL.h> header file.])
		AC_DEFINE([HAVE_LIBXPL], [1],
				[Define to 1 if you have the xPL library.])
	], [	AC_MSG_WARN([xPLLib required unit32_t type missing])])
	], [	AC_MSG_WARN([xPLLib required inet_ntoa function missing])])
	], [	AC_MSG_WARN([xPLLib required bzero function missing])])
	], [	AC_MSG_WARN([xPLLib required netinet/in.h header missing])])
	], [	AC_MSG_WARN([xPLLib required arpa/inet.h header missing])])
	], [	AC_MSG_WARN([xPLLib required header/function/type missing])])
	AS_IF([test "x$ac_cv_type_uint32_t" != xyes ], [AC_MSG_FAILURE(
			[Please try building and installing xPLLib apart,
			or reconfigure Heyu without xPL support selected])])])
AM_CONDITIONAL([XPLLIB_SRCDIR], [test "x$xPLLib_srcdir" != x])
AM_CONDITIONAL([XPLLIB_ARCHIVE], [test "x$xPLLib_archive" != x])
AM_CONDITIONAL([XPLLIB_URL], [test "x$xPLLib_URL" != x])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
