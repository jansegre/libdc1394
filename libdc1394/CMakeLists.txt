cmake_minimum_required(VERSION 2.8)

project(libdc1394)

add_subdirectory(dc1394)
if(EXAMPLES)
    add_subdirectory(examples)
endif()


#original Makefile.am contents follow:

## process this file with automake to create a Makefile.in
#
#SUBDIRS = dc1394
#if MAKE_EXAMPLES
#SUBDIRS += examples
#endif
#
#MAINTAINERCLEANFILES = Makefile.in aclocal.m4 configure config.h.in \
#	stamp-h.in
#EXTRA_DIST = libdc1394-2.pc.in Doxyfile.in INSTALL-windows README-windows
## Doxygen part
#MOSTLYCLEANFILES = $(DX_CLEANFILES)
#include $(top_srcdir)/aminclude.am
## pkg-config part
#pkgconfigdir = $(libdir)/pkgconfig
#pkgconfig_DATA = libdc1394-2.pc
#
