# Add search paths
# ----------------
include_directories(${OPENNI_INCLUDE_DIR}
					${XNCORE_INCLUDE_DIR}
					../
)

# Get sources
# ------------
file(GLOB ${XNDDK_LIB_NAME}_sources ./*.cpp)

# Add the library
# ---------------
add_library(
	${XNDDK_LIB_NAME} 
	SHARED 
	${${XNDDK_LIB_NAME}_sources}
)

target_link_libraries(
	${XNDDK_LIB_NAME}
	${XNCORE_LIB_NAME}
	${OPENNI_NIMCODECS_LIB_NAME}
	${LIBJPEG_LIB_NAME}
	${XNFORMAT_LIB_NAME}
)

# The install_name is Mac OSX specific and is used to set the RPATH on a executable
# On Mac OSX the library can hold information for the rpath of the executable which 
# uses the library.
# ----------------------------------------------------------------------------------
if(SENSOR_PLATFORM_MAC)
	set_target_properties(${XNDDK_LIB_NAME} PROPERTIES 
		BUILD_WITH_INSTALL_RPATH ON
		INSTALL_NAME_DIR ${INSTALL_NAME_VALUE}
	)
endif()

# Set install dir
# ---------------
install(
	TARGETS ${XNDDK_LIB_NAME}
	LIBRARY DESTINATION ${LIB_INSTALL_PATH}
	RUNTIME DESTINATION ${BIN_INSTALL_PATH}
)

