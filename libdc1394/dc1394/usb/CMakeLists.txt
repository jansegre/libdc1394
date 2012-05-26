cmake_minimum_required(VERSION 2.8)

add_library(libdc1394-usb STATIC
    control.c
    capture.c
    usb.h
)


#original Makefile.am contents follow:

#pkgusbincludedir = $(pkgincludedir)/usb
#
#if HAVE_LIBUSB
#noinst_LTLIBRARIES = libdc1394-usb.la
#
## headers to be installed
#pkgusbinclude_HEADERS = 
#endif
#
#AM_CFLAGS = -I$(top_srcdir)/dc1394 $(LIBUSB_CFLAGS)
#libdc1394_usb_la_LIBADD = $(LIBUSB_LIBS)
#libdc1394_usb_la_SOURCES =  \
#	control.c \
#	usb.h \
#	capture.c
#
