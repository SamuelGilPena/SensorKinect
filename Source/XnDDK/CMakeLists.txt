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

# Set install dir
# ---------------
install(
	TARGETS ${XNDDK_LIB_NAME}
	LIBRARY DESTINATION .
	RUNTIME DESTINATION .
)

