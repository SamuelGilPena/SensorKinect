cmake_minimum_required(VERSION 2.8)

project(SensorKinect)

# Options
# -------
option(CREATE_TEST_BUILD "Create a test build which you do no have to install" OFF)
option(CREATE_OF_BUILD "Create a build for the ofxOpenNI addon" OFF)

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
if(CREATE_TEST_BUILD)
	set(OPENNI_BASE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI/")
	set(OPENNI_NIMCODECS_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_TEST/lib/libnimCodecs.dylib")  
	set(OPENNI_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_TEST/lib/libOpenNI.dylib")
	set(LIBJPEG_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_TEST/lib/libJPEG.dylib")
	set(OPENNI_NIMCODECS_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_TEST/lib/libnimCodecs.dylib")

	# set the install paths for libraries and binaries
	# ------------------------------------------------
	set(INSTALL_NAME_VALUE "@executable_path/../lib")
	set(LIB_INSTALL_PATH "./lib/")
	set(BIN_INSTALL_PATH "./bin/")
	set(INCLUDE_FILES_INSTALL_PATH "include/")
elseif(CREATE_OF_BUILD)
        set(OF_OPENNI_DATA_DIR "../../../data/openni/")
<<<<<<< HEAD
	#set(OF_OPENNI_DATA_DIR "./../../../../../../../addons/ofxOpenNI/")	
=======
	
>>>>>>> d12a651f92a21bca4e472cc03d52a43183f89132
	set(OPENNI_BASE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI/")
        set(OPENNI_NIMCODECS_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_openFrameworks/lib/libnimCodecs.dylib")  
        set(OPENNI_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_openFrameworks/lib/libOpenNI.dylib")
        set(LIBJPEG_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_openFrameworks/lib/libJPEG.dylib")
        set(OPENNI_NIMCODECS_LIB_NAME "${CMAKE_CURRENT_SOURCE_DIR}/../OpenNI_openFrameworks/lib/libnimCodecs.dylib")

        # set the install paths for libraries and binaries
        # ------------------------------------------------
<<<<<<< HEAD
	#set(INSTALL_NAME_VALUE "@executable_path/${OF_OPENNI_DATA_DIR}lib/osx")
	set(INSTALL_NAME_VALUE "@executable_path/${OF_OPENNI_DATA_DIR}lib")
        set(LIB_INSTALL_PATH "./openni/lib/")
=======
	set(INSTALL_NAME_VALUE "@executable_path/${OF_OPENNI_DATA_DIR}lib")
        set(LIB_INSTALL_PATH "./lib/")
>>>>>>> d12a651f92a21bca4e472cc03d52a43183f89132
        set(BIN_INSTALL_PATH "./bin/")
        set(INCLUDE_FILES_INSTALL_PATH "include/")
	set(CMAKE_OSX_ARCHITECTURES "i386;x86_64")
endif()

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


# Add the sub-cmakefiles.txt
# --------------------------
add_subdirectory("./Source/XnCore/")
add_subdirectory("./Source/XnFormats/")
add_subdirectory("./Source/XnDDK/")
add_subdirectory("./Source/XnDeviceFile/")
add_subdirectory("./Source/XnDeviceSensorV2/")
add_subdirectory("./Source/Utils/XnSensorServer/")
