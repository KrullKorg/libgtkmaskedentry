SUBDIRS = icons

glademodulesdir = `pkg-config --variable=moduledir gladeui-2.0`

gladecatalogsdir = `pkg-config --variable=catalogdir gladeui-2.0`

gladecatalogs_DATA = gtkmaskedentry.xml

EXTRA_DIST = $(gladecatalogs_DATA)

if PLATFORM_WIN32
libmodulesext = -0.dll
libmodulesextglade = .dll
libmodulesdir = $(bindir)
else
libmodulesext = .so
libmodulesextglade = $(libmodulesext)
libmodulesdir = $(libdir)
endif

install-exec-hook:
	cd $(glademodulesdir) && \
	ln -s -f $(libmodulesdir)/libgtkmaskedentry$(libmodulesext) libgtkmaskedentry$(libmodulesextglade)

uninstall-hook:
	rm -f $(glademodulesdir)/libgtkmaskedentry$(libmodulesext)
