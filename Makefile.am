DISTCHECK_CONFIGURE_FLAGS = --disable-icon-mapping

SUBDIRS = $(SVGSRCDIR)

theme_in_files = index.theme.in.in
theme_DATA = $(theme_in_files:.theme.in.in=.theme)

THEME_DIRS=$(shell SIZES="$(render_sizes)"; for size in $$SIZES; do for dir in `find $(srcdir)/$(SVGOUTDIR)/$$size/* -type d`; do printf "$$dir,"; done; done | sed -e "s/,$$//g")

render: Makefile
	($(am__cd) $(SVGSRCDIR) && $(MAKE) $(AM_MAKEFLAGS) render) \
	|| eval `exit 1`

# we don't want to install mo files, all translations are already stored
# in theme files
install-data-local:
	if [ -h $(DESTDIR)$(themedir) ]; then \
		rm -f $(DESTDIR)$(themedir); \
	fi
	if [ -d $(DESTDIR)$(themedir) ]; then \
		touch $(DESTDIR)$(themedir); \
	fi

pkgconfigdir = $(datadir)/pkgconfig
pkgconfig_DATA = gnome-icon-theme.pc

EXTRA_DIST =			\
	gnome-icon-theme.pc.in  \
	gnome			\
	$(theme_in_files)

CLEANFILES = 			\
	$(theme_DATA)

MAINTAINERCLEANFILES =			\
	Makefile.in			\
	aclocal.m4			\
	config.guess			\
	config.h.in			\
	config.sub			\
	configure			\
	depcomp				\
	install-sh			\
	intltool-*.in			\
	libtool				\
	ltmain.sh			\
	missing				\
	mkinstalldirs
