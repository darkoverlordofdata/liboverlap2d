### CMakeLists automatically created with AutoVala
### Do not edit

set (DATADIR "${CMAKE_INSTALL_PREFIX}/${CMAKE_INSTALL_DATAROOTDIR}")
set (PKGDATADIR "${DATADIR}/libo2d")
set (GETTEXT_PACKAGE "libo2d")
set (RELEASE_NAME "libo2d")
set (CMAKE_C_FLAGS "")
set (PREFIX ${CMAKE_INSTALL_PREFIX})
set (VERSION "0.0.1")
set (TESTSRCDIR "${CMAKE_SOURCE_DIR}")
set (DOLLAR "$")

configure_file (${CMAKE_SOURCE_DIR}/src/Config.vala.cmake ${CMAKE_BINARY_DIR}/src/Config.vala)
add_definitions(-DGETTEXT_PACKAGE=\"${GETTEXT_PACKAGE}\")
configure_file (${CMAKE_CURRENT_SOURCE_DIR}/o2d.pc ${CMAKE_CURRENT_BINARY_DIR}/o2d.pc)
configure_file (${CMAKE_CURRENT_SOURCE_DIR}/o2d.deps ${CMAKE_CURRENT_BINARY_DIR}/o2d.deps)
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
set (APP_SOURCES ${APP_SOURCES} ParseIt.gs)
set (APP_SOURCES ${APP_SOURCES} SceneLoader.gs)
set (APP_SOURCES ${APP_SOURCES} ToString.gs)
set (APP_SOURCES ${APP_SOURCES} data/CompositeItemVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/CompositeVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/CoreActorData.gs)
set (APP_SOURCES ${APP_SOURCES} data/Image9patchVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/LabelVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/LayerItemVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/MainItemVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/PhysicsBodyDataVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/PhysicsPropertiesVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/PointVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/ProjectInfoVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/ResolutionEntryVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/SceneVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/ShapeVO.gs)
set (APP_SOURCES ${APP_SOURCES} data/SimpleImageVO.gs)
set (APP_SOURCES ${APP_SOURCES} resources/IAssetLoader.gs)
set (APP_SOURCES ${APP_SOURCES} resources/IDataLoader.gs)
set (APP_SOURCES ${APP_SOURCES} resources/IResourceRetriever.gs)
set (APP_SOURCES ${APP_SOURCES} resources/ResourceManager.gs)
set (APP_SOURCES ${APP_SOURCES} scene2d/BuiltItemHandler.gs)
set (APP_SOURCES ${APP_SOURCES} scene2d/ButtonClickListener.gs)
set (APP_SOURCES ${APP_SOURCES} scene2d/CompositeActor.gs)
set (APP_SOURCES ${APP_SOURCES} utils/CustomVariables.gs)

set (CUSTOM_VAPIS_LIST ${CUSTOM_VAPIS_LIST} ${CMAKE_SOURCE_DIR}/src/vapis/SDL2_image.vapi)
set (CUSTOM_VAPIS_LIST ${CUSTOM_VAPIS_LIST} ${CMAKE_SOURCE_DIR}/src/vapis/SDL2_mixer.vapi)
set (CUSTOM_VAPIS_LIST ${CUSTOM_VAPIS_LIST} ${CMAKE_SOURCE_DIR}/src/vapis/SDL2_ttf.vapi)
set (CUSTOM_VAPIS_LIST ${CUSTOM_VAPIS_LIST} ${CMAKE_SOURCE_DIR}/src/vapis/entitas.vapi)
set (CUSTOM_VAPIS_LIST ${CUSTOM_VAPIS_LIST} ${CMAKE_SOURCE_DIR}/src/vapis/sdl2.vapi)
set (CUSTOM_VAPIS_LIST ${CUSTOM_VAPIS_LIST} ${CMAKE_SOURCE_DIR}/src/vapis/sdx.vapi)


if ((${CMAKE_BUILD_TYPE} STREQUAL "Debug") OR (${CMAKE_BUILD_TYPE} STREQUAL "RelWithDebInfo"))
	set(COMPILE_OPTIONS ${COMPILE_OPTIONS} "-g")
endif()

set (COMPILE_OPTIONS ${COMPILE_OPTIONS} --library=o2d --gir o2d-0.0.gir )

vala_precompile(VALA_C o2d
	${APP_SOURCES}
PACKAGES
	${VALA_PACKAGES}
CUSTOM_VAPIS
	${CUSTOM_VAPIS_LIST}
OPTIONS
	${COMPILE_OPTIONS}
GENERATE_VAPI
	o2d
GENERATE_HEADER
	o2d
)

add_library(o2d SHARED ${VALA_C})

set_target_properties( o2d PROPERTIES
VERSION
	0.0.1
SOVERSION
	0 )


install(TARGETS
	o2d
LIBRARY DESTINATION
	${CMAKE_INSTALL_LIBDIR}/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/o2d.h
DESTINATION
	${CMAKE_INSTALL_INCLUDEDIR}/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/o2d.vapi
DESTINATION
	${CMAKE_INSTALL_DATAROOTDIR}/vala/vapi/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/o2d.deps
DESTINATION
	${CMAKE_INSTALL_DATAROOTDIR}/vala/vapi/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/o2d-0.0.gir
DESTINATION
	${CMAKE_INSTALL_DATAROOTDIR}/gir-1.0/
)
install(FILES
	${CMAKE_CURRENT_BINARY_DIR}/o2d.pc
DESTINATION
	${CMAKE_INSTALL_LIBDIR}/pkgconfig/
)
if(HAVE_VALADOC)
	valadoc(o2d
		${CMAKE_BINARY_DIR}/valadoc/o2d
		${APP_SOURCES}
	PACKAGES
		${VALA_PACKAGES}
	CUSTOM_VAPIS
		${CUSTOM_VAPIS_LIST}
	)
	install(DIRECTORY
		${CMAKE_BINARY_DIR}/valadoc
	DESTINATION
		${CMAKE_INSTALL_DATAROOTDIR}/doc/libo2d
	)
endif()

install(CODE "MESSAGE (\"
************************************************
* Run 'sudo ldconfig' to complete installation *
************************************************

\") " )