option(ENABLE_GTK_MODULE_DEMOS "Enable demo programs for gtk module" OFF)

pkg_check_modules(GTK2
    gtk+-2.0>=2.24)
find_package(X11)

pkg_check_modules(DOC gtk-doc>=1.26)
if(DOC_FOUND)
	add_subdirectory(docs)
endif()

set(LIB_PUBLIC_HEADERS
	lib/unity-gtk-parser.h
	lib/unity-gtk-menu-shell.h
	lib/unity-gtk-action-group.h)

set(GTK_MODULE_INCLUDE_DIR ${CMAKE_INSTALL_INCLUDEDIR}/appmenu-gtk-module)

install(FILES ${LIB_PUBLIC_HEADERS} DESTINATION ${GTK_MODULE_INCLUDE_DIR})

add_subdirectory(data)
add_subdirectory(lib)
add_subdirectory(src)
add_subdirectory(tests)
