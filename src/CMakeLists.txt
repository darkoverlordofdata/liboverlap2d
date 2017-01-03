### CMakeLists automatically created with AutoVala
### Do not edit

set (DATADIR "${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_DATAROOTDIR}")
set (PKGDATADIR "${DATADIR}/liboverlap2d")
set (GETTEXT_PACKAGE "liboverlap2d")
set (RELEASE_NAME "liboverlap2d")
set (CMAKE_C_FLAGS "")
set (PREFIX ${CMAKE_INSTALL_PREFIX})
set (VERSION "1.0.0")
set (TESTSRCDIR "${CMAKE_SOURCE_DIR}")
set (DOLLAR "$")

configure_file (${CMAKE_SOURCE_DIR}/src/Config.vala.cmake ${CMAKE_BINARY_DIR}/src/Config.vala)
add_definitions(-DGETTEXT_PACKAGE=\"${GETTEXT_PACKAGE}\")
set (VERSION "1.0.0")
add_definitions (${DEPS_CFLAGS})
link_libraries ( ${DEPS_LIBRARIES} )
link_directories ( ${DEPS_LIBRARY_DIRS} )
find_package (Vala REQUIRED)
include (ValaVersion)
ensure_vala_version ("0.30" MINIMUM)
include (ValaPrecompile)

set (VALA_PACKAGES ${VALA_PACKAGES} json-glib-1.0)
set (VALA_PACKAGES ${VALA_PACKAGES} gee-0.8)
set (VALA_PACKAGES ${VALA_PACKAGES} glib-2.0)
set (VALA_PACKAGES ${VALA_PACKAGES} gobject-2.0)

set (APP_SOURCES ${APP_SOURCES} ${CMAKE_CURRENT_BINARY_DIR}/Config.vala)
set (APP_SOURCES ${APP_SOURCES} Composite.gs)
set (APP_SOURCES ${APP_SOURCES} Image9patch.gs)
set (APP_SOURCES ${APP_SOURCES} Label.gs)
set (APP_SOURCES ${APP_SOURCES} Layer.gs)
set (APP_SOURCES ${APP_SOURCES} LibraryItem.gs)
set (APP_SOURCES ${APP_SOURCES} Overlap2D.gs)
set (APP_SOURCES ${APP_SOURCES} Physics.gs)
set (APP_SOURCES ${APP_SOURCES} PhysicsPropertiesVO.gs)
set (APP_SOURCES ${APP_SOURCES} Point.gs)
set (APP_SOURCES ${APP_SOURCES} Project.gs)
set (APP_SOURCES ${APP_SOURCES} Resolution.gs)
set (APP_SOURCES ${APP_SOURCES} Scene.gs)
set (APP_SOURCES ${APP_SOURCES} Shape.gs)
set (APP_SOURCES ${APP_SOURCES} liboverlap2d.vala)


if ((${CMAKE_BUILD_TYPE} STREQUAL "Debug") OR (${CMAKE_BUILD_TYPE} STREQUAL "RelWithDebInfo"))
	set(COMPILE_OPTIONS ${COMPILE_OPTIONS} "-g")
endif()

vala_precompile(VALA_C liboverlap2d
	${APP_SOURCES}
PACKAGES
	${VALA_PACKAGES}
)

add_executable(liboverlap2d ${VALA_C})


install(TARGETS
	liboverlap2d
RUNTIME DESTINATION
	${CMAKE_INSTALL_BINDIR}
)
if(HAVE_VALADOC)
	valadoc(liboverlap2d
		${CMAKE_BINARY_DIR}/valadoc/liboverlap2d
		${APP_SOURCES}
	PACKAGES
		${VALA_PACKAGES}
	CUSTOM_VAPIS
		${CUSTOM_VAPIS_LIST}
	)
	install(DIRECTORY
		${CMAKE_BINARY_DIR}/valadoc
	DESTINATION
		${CMAKE_INSTALL_DATAROOTDIR}/doc/liboverlap2d
	)
endif()
