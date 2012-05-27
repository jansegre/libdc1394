cmake_minimum_required(VERSION 2.8)

#TODO: Make a Find1394camera.
include_directories("C:\\Program Files (x86)\\CMU\\1394Camera\\include")

add_library(libdc1394-windows STATIC
    control.c
    capture.c
    platform_windows.h
)

target_link_libraries(libdc1394-windows
	Setupapi.lib
    "C:\\Program Files (x86)\\CMU\\1394Camera\\lib\\1394camera.lib"
)


#original Makefile.am contents follow:

#if HAVE_WINDOWS
#noinst_LTLIBRARIES = libdc1394-windows.la
#endif
#
#AM_CFLAGS = -DDC1394_DLL_EXPORTS -I$(top_srcdir) -I$(srcdir)/..
#libdc1394_windows_la_SOURCES = control.c capture.c platform_windows.h
