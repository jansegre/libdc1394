cmake_minimum_required(VERSION 2.8)

include_directories(. ..)

set(libdc1394_LIBS)

if(UNIX)
    #if HAVE_LIBRAW1394
        add_subdirectory(linux)
        list(APPEND libdc1394_LIBS libdc1394-linux)
    #endif
    add_subdirectory(juju)
    list(APPEND libdc1394_LIBS libdc1394-juju)
endif()

if(APPLE)
    add_subdirectory(macosx)
    list(APPEND libdc1394_LIBS libdc1394-macosx)
endif()

if(WIN32)
    add_subdirectory(windows)
    list(APPEND libdc1394_LIBS libdc1394-windows)
endif()

if(MSVC)
    include_directories(../includes/msvc)
endif()

#TODO:
#find_package(LibUSB)
#if(LIBUSB_FOUND)
#    add_subdirectory(usb)
#    list(APPEND libdc1394_LIBS libdc1394-usb)
#endif()

add_subdirectory(vendor)
list(APPEND libdc1394_LIBS libdc1394-vendor)


########### next target ###############

add_library(libdc1394
    control.c
    control.h
    enumeration.c
    platform.h
    capture.c
    offsets.h
    format7.c
    register.c
    register.h
    utils.c
    utils.h
    internal.c
    internal.h
    conversions.c
    conversions.h
    bayer.c
    log.c
    log.h
    iso.c
    iso.h
)

target_link_libraries(libdc1394 ${libdc1394_LIBS})
#set_target_properties(libdc1394 PROPERTIES VERSION 1.0.0 SOVERSION 1)


#original Makefile.am contents follow:

#MAINTAINERCLEANFILES = Makefile.in
#lib_LTLIBRARIES = libdc1394.la
#
#SUBDIRS = linux juju macosx windows usb vendor
#AM_CFLAGS = $(platform_CFLAGS) -I$(top_srcdir)
#
#libdc1394_la_LDFLAGS = $(platform_LDFLAGS) \
#	-version-info @lt_current@:@lt_revision@:@lt_age@
#
#libdc1394_la_SOURCES =  \
#	control.c 	\
#	control.h	\
#	enumeration.c   \
#	platform.h      \
#	capture.c       \
#	offsets.h	\
#	format7.c       \
#	register.c      \
#	register.h      \
#	utils.c         \
#	utils.h         \
#	internal.c      \
#	internal.h      \
#	conversions.c   \
#	conversions.h   \
#	bayer.c         \
#	log.c		\
#	log.h		\
#	iso.c 		\
#	iso.h
#
#if HAVE_LINUX
#if HAVE_LIBRAW1394
#  LINUX_LIBADD = linux/libdc1394-linux.la
#endif
#  JUJU_LIBADD = juju/libdc1394-juju.la
#endif
#if HAVE_MACOSX
#  MACOSX_LIBADD = macosx/libdc1394-macosx.la
#endif
#if HAVE_WINDOWS
#  WINDOWS_LIBADD = windows/libdc1394-windows.la
#endif
#if HAVE_LIBUSB
#  USB_LIBADD = usb/libdc1394-usb.la
#endif
#
#libdc1394_la_LIBADD = \
#	$(LINUX_LIBADD) \
#	$(JUJU_LIBADD) \
#	$(MACOSX_LIBADD) \
#	$(WINDOWS_LIBADD) \
#	$(USB_LIBADD) \
#	vendor/libdc1394-vendor.la
#
## headers to be installed
#pkginclude_HEADERS =  	\
#	dc1394.h	\
#	types.h		\
#	camera.h	\
#	control.h     	\
#	capture.h	\
#	video.h		\
#	format7.h	\
#	utils.h       	\
#	conversions.h 	\
#	register.h    	\
#	log.h	      	\
#	iso.h
