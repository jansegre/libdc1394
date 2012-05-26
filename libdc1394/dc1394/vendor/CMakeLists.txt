cmake_minimum_required(VERSION 2.8)

add_library(libdc1394-vendor STATIC
    avt.c
    avt.h
    pixelink.c
    pixelink.h
    basler.c
    basler_sff_registry.h
    basler_sff_registry.c
)


#original Makefile.am contents follow:

#noinst_LTLIBRARIES = libdc1394-vendor.la
#
#pkgvendorincludedir = $(pkgincludedir)/vendor
#
#AM_CFLAGS = -I$(top_srcdir) -I$(srcdir)/..
#libdc1394_vendor_la_SOURCES =  \
#	avt.c \
#	avt.h \
#	pixelink.c \
#	pixelink.h \
#	basler.c \
#	basler_sff_registry.h \
#	basler_sff_registry.c
#
## headers to be installed
#pkgvendorinclude_HEADERS = \
#	avt.h \
#	pixelink.h \
#	basler.h \
#	basler_sff.h
#
