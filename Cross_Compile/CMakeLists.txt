# TheNaserov
# REF : https://cmake.org/cmake/help/book/mastering-cmake/chapter/Cross%20Compiling%20With%20CMake.html

# the name of the target operating system
set(CMAKE_SYSTEM_NAME Windows)

# which compilers to use for C and C++
set(CMAKE_C_COMPILER   i586-mingw32msvc-gcc)
set(CMAKE_CXX_COMPILER i586-mingw32msvc-g++)

# where is the target environment located
set(CMAKE_FIND_ROOT_PATH  /usr/i586-mingw32msvc
    /home/thenaserov/mingw-install)

# adjust the default behavior of the FIND_XXX() commands:
# search programs in the host environment
set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)

# search headers and libraries in the target environment
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)


# how to build
# ~/src$ cd build
# ~/src/build$ cmake -DCMAKE_TOOLCHAIN_FILE=~/TC-mingw.cmake ..
# ...


# to use cmake command to build using a custom compiler >>
# cmake -G "Visual Studio 9 2008 Win64" -Wno-dev -DCMAKE_BUILD_TYPE=Debug -DCMAKE_INSTALL_PREFIX=..\..\Marble-Bin\Debug -DCMAKE_CXX_COMPILER=/path/to/your/compiler ..\..\Marble-Src
# this was an example to do it for marble maps compilation so if you want the general idea >>
# cmake -Wno-dev -DCMAKE_BUILD_TYPE=Debug -DCMAKE_C_COMPILER=<C-COMPILER-PATH> -DCMAKE_CXX_COMPILER=<CXX-COMPILER-PATH> -DCMAKE_BUILD_TYPE=Debug|Release -DCMAKE_INSTALL_PREFIX=<INSTALLATION DIR> <the path to the CMakeLists.txt file that CMake will use to generate the build system>


# ------------------------------------------------------------------------------------------------------------------------------------------------------
# THE ONE I DID FOR MAPNA
# I GOT THE TOOLCHAIN FROM ARASH AND MADE A TOOLCHAIN.CMAKE AND RAN CMAKE AND MAKE
# SYNTAX TO RUN IN TERMINAL "cmake -DCMAKE_TOOLCHAIN_FILE=<.cmake path> <path to CMakeLists.txt project>"
# EXAMPLE -> cmake -DCMAKE_TOOLCHAIN_FILE=../toolchain.cmake ../../
# ------------------------------------------------------------------------------------------------------------------------------------------------------
set(CMAKE_SYSTEM_NAME Linux)  # Or the target system name
set(CMAKE_SYSTEM_PROCESSOR arm)  # Or the target processor architecture


set(CMAKE_C_FLAGS "-O -mthumb -mfpu=neon -mfloat-abi=hard -mcpu=cortex-a7 -fstack-protector-strong  -D_FORTIFY_SOURCE=2 -Wformat -Wformat-security -Werror=format-security --sysroot=/opt/fsl-imx-fb/5.10-gatesgarth/sysroots/cortexa7t2hf-neon-poky-linux-gnueabi")
set(CMAKE_CXX_FLAGS "-O -mthumb -mfpu=neon -mfloat-abi=hard -mcpu=cortex-a7 -fstack-protector-strong  -D_FORTIFY_SOURCE=2 -Wformat -Wformat-security -Werror=format-security --sysroot=/opt/fsl-imx-fb/5.10-gatesgarth/sysroots/cortexa7t2hf-neon-poky-linux-gnueabi")


set(CMAKE_C_COMPILER /opt/fsl-imx-fb/5.10-gatesgarth/sysroots/x86_64-pokysdk-linux/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-gcc)
set(CMAKE_CXX_COMPILER /opt/fsl-imx-fb/5.10-gatesgarth/sysroots/x86_64-pokysdk-linux/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-g++)


set(CMAKE_SYSROOT /opt/fsl-imx-fb/5.10-gatesgarth/sysroots/cortexa7t2hf-neon-poky-linux-gnueabi)

#set(CMAKE_C_COMPILER /opt/fsl-imx-fb/5.10-gatesgarth/sysroots/x86_64-pokysdk-linux/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-gcc)
#set(CMAKE_CXX_COMPILER /opt/fsl-imx-fb/5.10-gatesgarth/sysroots/x86_64-pokysdk-linux/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-g++)

#set(CMAKE_C_COMPILER arm-poky-linux-gnueabi-gcc)
#set(CMAKE_CXX_COMPILER arm-poky-linux-gnueabi-g++)

#set(CMAKE_C_COMPILER "$CC")
#set(CMAKE_CXX_COMPILER "$CXX")

set(CMAKE_FIND_ROOT_PATH $PATH)
include_directories("${CMAKE_SYSROOT}/usr/include")
link_directories("${CMAKE_SYSROOT}/usr/lib")

set(CMAKE_FIND_ROOT_PATH_MODE_PROGRAM NEVER)
set(CMAKE_FIND_ROOT_PATH_MODE_LIBRARY ONLY)
set(CMAKE_FIND_ROOT_PATH_MODE_INCLUDE ONLY)


