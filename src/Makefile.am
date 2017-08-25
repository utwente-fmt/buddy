AM_CPPFLAGS = -I$(top_builddir)

include_HEADERS = bdd.h fdd.h bvec.h

lib_LTLIBRARIES = libbdd.la
libbdd_la_SOURCES = \
 bddio.c \
 bddop.c \
 bddtree.h \
 bvec.c \
 cache.c \
 cache.h \
 cppext.cxx \
 fdd.c \
 imatrix.c \
 imatrix.h \
 kernel.c \
 kernel.h \
 pairs.c \
 prime.c \
 prime.h \
 reorder.c \
 tree.c

# See the `Updating version info' node of the Libtool manual before
# changing this.
libbdd_la_LDFLAGS = -version-info 0:0:0
libbdd_la_LIBADD = -lm

check_PROGRAMS = bddtest
bddtest_SOURCES = bddtest.cxx
bddtest_LDADD = ./libbdd.la

EXTRA_DIST = $(srcdir)/libbdd.pc.in
pkgconfigdir = $(libdir)/pkgconfig
nodist_pkgconfig_DATA = libbdd.pc

libbdd.pc: $(srcdir)/libbdd.pc.in Makefile
	sed -e 's![@]prefix[@]!$(prefix)!g' \
	    -e 's![@]exec_prefix[@]!$(exec_prefix)!g' \
	    -e 's![@]includedir[@]!$(includedir)!g' \
	    -e 's![@]libdir[@]!$(libdir)!g' \
	    -e 's![@]PACKAGE_VERSION[@]!$(PACKAGE_VERSION)!g' \
	$(srcdir)/libbdd.pc.in >$@.tmp && mv $@.tmp $@

CLEANFILES = libbdd.pc
