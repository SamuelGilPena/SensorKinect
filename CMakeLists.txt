cmake_minimum_required(VERSION 2.8)

project(SensorKinect)

# Check the system
# ----------------
if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
	set(SENSOR_PLATFORM_LINUX true)
elseif(WIN32)
	set(SENSOR_PLATFORM_WIN32 true)
elseif(APPLE)
	set(SENSOR_PLATFORM_MAC true)
endif()

# Some global variables
# ---------------------
# @todo create find modules for openni!
#set(OPENNI_BASE_DIR "/home/roxlu/Documents/programming/c++/openni_fork/")
set(OPENNI_BASE_DIR "/Users/diederickhuijbers/Documents/programming/c++/__PLAYGROUND__/openni/")

set(OPENNI_LIB_NAME "${OPENNI_BASE_DIR}/Platform/Mac/Bin/Release/libOpenNI.dylib")
set(XNCORE_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/Include/")
set(XNCORE_LIB_NAME "XnCore")
set(XNDDK_LIB_NAME "XnDDK")
set(XNFORMAT_LIB_NAME "XnFormats")
set(XNDEVICEFILE_LIB_NAME "XnDeviceFile")
set(XNDEVICESENSOR_LIB_NAME "XnDevicesSensorV2")
set(XNSENSORSERVER_TARGET_NAME "XnSensorServer")
set(OPENNI_INCLUDE_DIR "${OPENNI_BASE_DIR}/Include/")
set(OPENNI_LIB_DIR "${OPENNI_BASE_DIR}/Platform/Mac/Bin/Release/")
set(LIBJPEG_INCLUDE_DIR "${OPENNI_BASE_DIR}/Source/External/LibJPEG/")

# for mac
set(OPENNI_NIMCODECS_LIB_NAME "${OPENNI_BASE_DIR}Platform/Mac/Bin/Release/libnimCodecs.dylib") # @todo we need to fix this!!

# @todo make a find which searches for OpenNI, libJPEG and TinyXML.so 
#set(LIBJPEG_LIB_NAME "/home/roxlu/Documents/programming/c++/sensorkinect/Platform/test/libJPEG.so")
set(LIBJPEG_LIB_NAME "/Users/diederickhuijbers/Documents/programming/c++/__PLAYGROUND__/openni/Platform/Mac/Bin/Release/libJPEG.dylib")

# Add the sub-cmakefiles.txt
# --------------------------
add_subdirectory("./Source/XnCore/")
add_subdirectory("./Source/XnFormats/")
add_subdirectory("./Source/XnDDK/")
add_subdirectory("./Source/XnDeviceFile/")
add_subdirectory("./Source/XnDeviceSensorV2/")
add_subdirectory("./Source/Utils/XnSensorServer/")
