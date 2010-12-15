# Add search paths
# ----------------
include_directories(${OPENNI_INCLUDE_DIR}
					${XNCORE_INCLUDE_DIR}
					${LIBJPEG_INCLUDE_DIR}
					../
)

# Get sources
# ------------
file(GLOB ${XNDEVICESENSOR_LIB_NAME}_sources ./*.cpp)

# Add the library
# ---------------
add_library(
	${XNDEVICESENSOR_LIB_NAME} 
	SHARED 
	${${XNDEVICESENSOR_LIB_NAME}_sources}
)

# Set install dir
# ---------------
install(
	TARGETS ${XNDEVICESENSOR_LIB_NAME}
	LIBRARY DESTINATION .
	RUNTIME DESTINATION .
)

