## Process this file with automake to produce Makefile.in

bin_PROGRAMS = advscan advdiff

advdiff_SOURCES = \
	diff.cc \
	rom.cc \
	disk.cc \
	sample.cc \
	data.cc \
	strcov.c \
	file.cc \
	ziprom.cc \
	game.cc \
	gameinfo.cc \
	gamexml.cc \
	zip.cc \
	siglock.cc \
	getopt.c \
	snprintf.c \
	lib/readinfo.c \
	expat/xmlrole.c \
	expat/xmlparse.c \
	expat/xmltok.c

advscan_SOURCES =  \
	scan.cc \
	rom.cc \
	disk.cc \
	sample.cc \
	conf.cc \
	data.cc \
	token.cc \
	strcov.c \
	file.cc \
	ziprom.cc \
	game.cc \
	gameinfo.cc \
	gamexml.cc \
	zip.cc \
	output.cc \
	analyze.cc \
	siglock.cc \
	getopt.c \
	snprintf.c \
	lib/readinfo.c \
	expat/xmlrole.c \
	expat/xmlparse.c \
	expat/xmltok.c

EXTRA_DIST = advscan.rc.linux advscan.rc.dos \
	README AUTHORS HISTORY INSTALL COPYING \
	doc/advscan.d doc/advdiff.d doc/history.d doc/readme.d doc/authors.d doc/install.d \
	doc/advscan.1 doc/advdiff.1 doc/history.1 doc/readme.1 doc/authors.1 doc/install.1 \
	doc/advscan.txt doc/advdiff.txt doc/history.txt doc/readme.txt doc/authors.txt doc/install.txt \
	doc/advscan.html doc/advdiff.html doc/history.html doc/readme.html doc/authors.html doc/install.html \
	autogen.sh noautomake.sh \
	test/test.xml \
	test/test.lst \
	test/testd.xml \
	test/testd.lst

noinst_HEADERS = \
	snprintf.c \
	rom.h \
	sample.h \
	disk.h \
	data.h \
	token.h \
	strcov.h \
	file.h \
	conf.h \
	ziprom.h \
	game.h \
	zip.h \
	except.h \
	output.h \
	operatio.h \
	analyze.h \
	analyze.dat \
	siglock.h \
	portable.h \
	lib/readinfo.h \
	lib/endianrw.h \
	lib/extra.h \
	expat/COPYING \
	expat/README \
	expat/ascii.h \
	expat/asciitab.h \
	expat/expat-1.95.8.diff \
	expat/expat.h \
	expat/iasciitab.h \
	expat/expatcfg.h \
	expat/expat_external.h \
	expat/internal.h \
	expat/latin1tab.h \
	expat/nametab.h \
	expat/utf8tab.h \
	expat/xmlparse.c \
	expat/xmlrole.c \
	expat/xmlrole.h \
	expat/xmltok.c \
	expat/xmltok.h \
	expat/xmltok_impl.c \
	expat/xmltok_impl.h \
	expat/xmltok_ns.c

man_MANS = doc/advscan.1 doc/advdiff.1

clean-local:
	rm -f advscan.exe advscan.rc advdiff.exe
	rm -f check.lst checkd.lst

maintainer-clean-local:
	rm -f README AUTHORS HISTORY INSTALL doc/copying.txt
	rm -f doc/*.hh

check-local:
	rm -f check.lst checkd.lst
	./advscan -e < $(srcdir)/test/test.xml > check.lst
	cmp check.lst $(srcdir)/test/test.lst
	./advdiff $(srcdir)/test/test.xml $(srcdir)/test/testd.xml > checkd.lst
	cmp checkd.lst $(srcdir)/test/testd.lst
	echo Success!

# Docs

%.1 : %.d
	advd2 man < $(srcdir)/$< > $@

%.txt : %.d
	advd2 txt < $(srcdir)/$< | todos > $@

%.html : %.d
	advd2 html < $(srcdir)/$< > $@

%.hh : %.d
	advd2 frame < $(srcdir)/$< > $@

# Archives

advscan.rc: advscan.rc.dos
	cp $(srcdir)/advscan.rc.dos advscan.rc

README: doc/readme.txt
	cat $< | fromdos > $@

AUTHORS: doc/authors.txt
	cat $< | fromdos > $@

INSTALL: doc/install.txt
	cat $< | fromdos > $@

HISTORY: doc/history.txt
	cat $< | fromdos > $@

doc/copying.txt: COPYING
	cat $< | todos > $@

DISTDOS_ROOT = \
	doc/readme.txt doc/authors.txt doc/history.txt doc/copying.txt \
	advscan.exe advdiff.exe \
	advscan.rc

DISTDOS_DOC = \
	doc/advscan.txt doc/advdiff.txt \
	doc/readme.txt doc/authors.txt doc/history.txt \
	doc/advscan.html doc/advdiff.html \
	doc/readme.html doc/authors.html doc/history.html 

distdos: $(DISTDOS_ROOT) $(DISTDOS_DOC)
	rm -f $(PACKAGE)-$(VERSION)-dos-pentium.zip
	mkdir tmp
	cp $(DISTDOS_ROOT) tmp
	mkdir tmp/doc
	cp $(DISTDOS_DOC) tmp/doc
	cd tmp && zip -r ../$(PACKAGE)-$(VERSION)-dos-pentium.zip *
	rm -r tmp

distwindows: $(DISTDOS_ROOT) $(DISTDOS_DOC)
	rm -f $(PACKAGE)-$(VERSION)-windows-pentium.zip
	mkdir tmp
	cp $(DISTDOS_ROOT) tmp
	mkdir tmp/doc
	cp support/zlib.dll tmp
	cp $(DISTDOS_DOC) tmp/doc
	cd tmp && zip -r ../$(PACKAGE)-$(VERSION)-windows-pentium.zip *
	rm -r tmp

DISTWEB = \
	doc/advscan.hh doc/advdiff.hh doc/history.hh

web: $(DISTWEB)

