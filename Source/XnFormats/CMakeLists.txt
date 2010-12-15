# Add search paths
# ----------------
include_directories(${OPENNI_INCLUDE_DIR}
					${XNCORE_INCLUDE_DIR}
					${LIBJPEG_INCLUDE_DIR}
					../
)

# Get sources
# ------------
file(GLOB ${XNFORMAT_LIB_NAME}_sources ./*.cpp)

# Add the library
# ---------------
add_library(
	${XNFORMAT_LIB_NAME} 
	SHARED 
	${${XNFORMAT_LIB_NAME}_sources}
)

target_link_libraries(
	${XNFORMAT_LIB_NAME}
	${LIBJPEG_LIB_NAME}
	${XNCORE_LIB_NAME}
)

# Set install dir
# ---------------
install(
	TARGETS ${XNFORMAT_LIB_NAME}
	LIBRARY DESTINATION .
	RUNTIME DESTINATION .
)

