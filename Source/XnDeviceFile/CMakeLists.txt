# Add search paths
# ----------------
include_directories(${OPENNI_INCLUDE_DIR}
					${XNCORE_INCLUDE_DIR}
					../
)

# Get sources
# ------------
file(GLOB ${XNDEVICEFILE_LIB_NAME}_sources ./*.cpp)

# Add the library
# ---------------
add_library(
	${XNDEVICEFILE_LIB_NAME} 
	SHARED 
	${${XNDEVICEFILE_LIB_NAME}_sources}
)

# Set install dir
# ---------------
install(
	TARGETS ${XNDEVICEFILE_LIB_NAME}
	LIBRARY DESTINATION .
	RUNTIME DESTINATION .
)

