### CMakeLists automatically created with AutoVala
### Do not edit

set (DATADIR "${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_DATAROOTDIR}")
set (PKGDATADIR "${DATADIR}/liboverlap2d")
set (GETTEXT_PACKAGE "liboverlap2d")
set (RELEASE_NAME "liboverlap2d")
set (CMAKE_C_FLAGS "")
set (PREFIX ${CMAKE_INSTALL_PREFIX})
set (VERSION "0.0.1")
set (TESTSRCDIR "${CMAKE_SOURCE_DIR}")
set (DOLLAR "$")

configure_file (${CMAKE_SOURCE_DIR}/src/Config.vala.cmake ${CMAKE_BINARY_DIR}/src/Config.vala)
add_definitions(-DGETTEXT_PACKAGE=\"${GETTEXT_PACKAGE}\")
configure_file (${CMAKE_CURRENT_SOURCE_DIR}/overlap2d.pc ${CMAKE_CURRENT_BINARY_DIR}/overlap2d.pc)
configure_file (${CMAKE_CURRENT_SOURCE_DIR}/overlap2d.deps ${CMAKE_CURRENT_BINARY_DIR}/overlap2d.deps)
set (VERSION "0.0.1")
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
set (APP_SOURCES ${APP_SOURCES} Data/CompositeItemVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/CompositeVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/Image9patchVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/LabelVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/LayerItemVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/MainItemVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/PhysicsBodyDataVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/PhysicsPropertiesVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/PointVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/ProjectInfoVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/ResolutionEntryVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/SceneVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/ShapeVO.gs)
set (APP_SOURCES ${APP_SOURCES} Data/SimpleImageVO.gs)
set (APP_SOURCES ${APP_SOURCES} Overlap2D.gs)
set (APP_SOURCES ${APP_SOURCES} ParseIt.gs)
set (APP_SOURCES ${APP_SOURCES} Resources/ResourceManager.gs)
set (APP_SOURCES ${APP_SOURCES} SceneLoader.gs)
set (APP_SOURCES ${APP_SOURCES} ToString.gs)


if ((${CMAKE_BUILD_TYPE} STREQUAL "Debug") OR (${CMAKE_BUILD_TYPE} STREQUAL "RelWithDebInfo"))
	set(COMPILE_OPTIONS ${COMPILE_OPTIONS} "-g")
endif()

set (COMPILE_OPTIONS ${COMPILE_OPTIONS} --library=overlap2d --gir overlap2d-0.0.gir )

vala_precompile(VALA_C overlap2d
	${APP_SOURCES}
PACKAGES
	${VALA_PACKAGES}
OPTIONS
	${COMPILE_OPTIONS}
GENERATE_VAPI
	overlap2d
GENERATE_HEADER
	overlap2d
)

add_library(overlap2d SHARED ${VALA_C})

set_target_properties( overlap2d PROPERTIES
VERSION
	0.0.1
SOVERSION
	0 )


install(TARGETS
	overlap2d
LIBRARY DESTINATION
	${CMAKE_INSTALL_LIBDIR}/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/overlap2d.h
DESTINATION
	${CMAKE_INSTALL_INCLUDEDIR}/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/overlap2d.vapi
DESTINATION
	${CMAKE_INSTALL_DATAROOTDIR}/vala/vapi/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/overlap2d.deps
DESTINATION
	${CMAKE_INSTALL_DATAROOTDIR}/vala/vapi/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/overlap2d-0.0.gir
DESTINATION
	${CMAKE_INSTALL_DATAROOTDIR}/gir-1.0/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/overlap2d.pc
DESTINATION
	${CMAKE_INSTALL_LIBDIR}/pkgconfig/
)
if(HAVE_VALADOC)
	valadoc(overlap2d
		${CMAKE_BINARY_DIR}/valadoc/overlap2d
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

install(CODE "MESSAGE (\"
************************************************
* Run 'sudo ldconfig' to complete installation *
************************************************

\") " )