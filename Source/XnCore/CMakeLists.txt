# Add search paths
# ----------------
include_directories(${OPENNI_INCLUDE_DIR})
include_directories(${XNCORE_INCLUDE_DIR})
include_directories(../)

# Get sources
# ------------
file(GLOB ${XNCORE_LIB_NAME}_sources ./*.cpp)

# Add the library
# ---------------
add_library(
	${XNCORE_LIB_NAME} 
	SHARED 
	${${XNCORE_LIB_NAME}_sources}
)

# Set link libraries
# -------------------
target_link_libraries(${XNCORE_LIB_NAME} ${OPENNI_LIB_NAME})
if(SENSOR_PLATFORM_MAC)
	set_target_properties(${XNCORE_LIB_NAME} PROPERTIES 
		BUILD_WITH_INSTALL_RPATH ON
		INSTALL_NAME_DIR ${INSTALL_NAME_VALUE}
	)
endif()

# Set install dir
# ---------------
install(
	TARGETS ${XNCORE_LIB_NAME}
	LIBRARY DESTINATION ${LIB_INSTALL_PATH}
	RUNTIME DESTINATION ${BIN_INSTALL_PATH}
)
