ACLOCAL_AMFLAGS = -I m4
AM_CFLAGS =

light_guid = f3e604dd-f4de-4311-88b0-7ac45cadc068
darker_guid = 8199d028-4c2c-4e4d-857f-23759b2579de
dark_guid = 2b61e02d-6a39-412b-937a-917c7f3bbefa

lighttempdir = $(top_builddir)/rsm-firefox-theme-light
darkertempdir = $(top_builddir)/rsm-firefox-theme-darker
darktempdir = $(top_builddir)/rsm-firefox-theme-darker

extensiondir = $(DESTDIR)/$(libdir)/firefox/browser/extensions


EXTRA_DIST = ${top_srcdir}/README.md \
	     ${top_srcdir}/LICENSE \
	     ${top_srcdir}/rsm-firefox-theme \
	     $(top_srcdir)/autogen.sh
NULL =


mkxpi:
if ENABLE_LIGHT
	cp -R $(top_srcdir)/rsm-firefox-theme $(lighttempdir)

	cp $(lighttempdir)/chrome/browser/sass/browser-light.css $(lighttempdir)/chrome/browser/browser.css
	rm -rf $(lighttempdir)/chrome/browser/sass
	rm $(lighttempdir)/chrome/overrides.sh

	cd $(lighttempdir) && \
		/usr/bin/zip -FS -r ../rsm-firefox-theme-$(VERSION).xpi *

	rm -rf $(lighttempdir)
endif # ENABLE_LIGHT

if ENABLE_DARKER
	cp -R $(top_srcdir)/rsm-firefox-theme $(darkertempdir)

	cp $(darkertempdir)/chrome/browser/sass/browser-darker.css $(darkertempdir)/chrome/browser/browser.css
	rm -rf $(darkertempdir)/chrome/browser/sass
	rm $(darkertempdir)/chrome/overrides.sh

	sed -i 's/rsm-theme/rsm-darker-theme/' $(darkertempdir)/chrome.manifest
	sed -i 's/rsm-theme/rsm-darker-theme/' $(darkertempdir)/install.rdf
	sed -i 's/RSM /RSM Darker /' $(darkertempdir)/install.rdf

	sed -i "s/$(light_guid)/$(darker_guid)/" $(darkertempdir)/install.rdf

	cd $(darkertempdir) && \
		/usr/bin/zip -FS -r ../rsm-darker-firefox-theme-$(VERSION).xpi *

	rm -rf $(darkertempdir)
endif # ENABLE_LIGHT

if ENABLE_DARK
	cp -R $(top_srcdir)/rsm-firefox-theme $(darktempdir)

	cp $(darktempdir)/chrome/browser/sass/browser-dark.css $(darktempdir)/chrome/browser/browser.css
	rm -rf $(darktempdir)/chrome/browser/sass
	rm $(darktempdir)/chrome/overrides.sh

	sed -i 's/rsm-theme/rsm-dark-theme/' $(darktempdir)/chrome.manifest
	sed -i 's/rsm-theme/rsm-dark-theme/' $(darktempdir)/install.rdf
	sed -i 's/RSM /RSM Dark /' $(darktempdir)/install.rdf

	sed -i "s/$(light_guid)/$(dark_guid)/" $(darktempdir)/install.rdf

	cd $(darktempdir) && \
		/usr/bin/zip -FS -r ../rsm-dark-firefox-theme-$(VERSION).xpi *

	rm -rf $(darktempdir)
endif # ENABLE_DARK

install-data-local: mkxpi

	$(MKDIR_P) $(extensiondir)

if ENABLE_LIGHT
	/usr/bin/unzip -d $(extensiondir)/\{$(light_guid)\} $(top_builddir)/rsm-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT

if ENABLE_DARKER
	/usr/bin/unzip -d $(extensiondir)/\{$(darker_guid)\} $(top_builddir)/rsm-darker-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT

if ENABLE_DARK
	/usr/bin/unzip -d $(extensiondir)/\{$(dark_guid)\} $(top_builddir)/rsm-dark-firefox-theme-$(VERSION).xpi
endif # ENABLE_LIGHT


uninstall:
if ENABLE_LIGHT
	rm -rf $(extensiondir)/\{$(light_guid)\}
endif # ENABLE_LIGHT

if ENABLE_DARKER
	rm -rf $(extensiondir)/\{$(darker_guid)\}
endif # ENABLE_DARKER

if ENABLE_DARK
	rm -rf $(extensiondir)/\{$(dark_guid)\}
endif # ENABLE_DARK

CLEANFILES = \
	rsm-firefox-theme-$(VERSION).xpi \
	rsm-darker-firefox-theme-$(VERSION).xpi \
	rsm-dark-firefox-theme-$(VERSION).xpi
