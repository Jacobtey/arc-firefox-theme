AC_INIT([rsm-firefox-theme], [49.20160920], [https://github.com/jacobtey/rsm-firefox-theme/issues], [rsm-firefox-theme], [https://github.com/jacobtey/rsm-firefox-theme])
AM_INIT_AUTOMAKE([-Wno-portability no-dist-gzip dist-xz foreign subdir-objects tar-ustar])
AC_PREFIX_DEFAULT(/usr/local)
AM_SILENT_RULES([yes])
AC_CONFIG_MACRO_DIR([m4])
AC_PROG_MKDIR_P


RSM_ENABLE([LIGHT],         [light],         [RSM Light Firefox],     [disable])
RSM_ENABLE([DARKER],        [darker],        [RSM Darker Firefox],    [disable])
RSM_ENABLE([DARK],          [dark],          [RSM Dark Firefox],      [disable])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

AC_MSG_RESULT([
        rsm-firefox-theme $VERSION
        ========

        prefix:                 ${prefix}
        exec_prefix:            ${exec_prefix}
        datarootdir:            ${datarootdir}
])
