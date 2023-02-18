# TCNOpenStaticLib
This is the static library (linux-x86) of [TCNOpen](https://github.com/T12z/TCNopen) project for train communication. 
Train real time data protocol [TRDP](https://de.wikipedia.org/wiki/Train_Real_Time_Data_Protocol) is the major protocol in
train communication network.

# Usage
1. Clone the repository, put the repository under your project's `include` foler.
2. In your code, include the needed librarys like this:
```
#include <TCNOpenStaticLib/api/trdp_if_light.h>
#include <TCNOpenStaticLib/api/tau_marshall.h>
#include <TCNOpenStaticLib/vos/api/vos_utils.h>
...
```
1. Then you are able to use the functions in the library, here you could file some [examples](https://github.com/T12z/TCNopen/tree/master/trdp/example) codes.
2. To compile your project with those libraries, link the static library in `CMakeLists.txt` file like this:
```
set(CMAKE_FIND_LIBRARY_SUFFIXES ".a")
set(CMAKE_EXE_LINKER_FLAGS "-static-libgcc -static-libstdc++ -static")
set(BUILD_SHARED_LIBS OFF)

add_library(${PROJECT_NAME} STATIC ${PROJECT_SOURCE})

target_link_libraries(${PROJECT_NAME} ${PROJECT_LIBS} ${PROJECT_SOURCE_DIR}/include/TCNOpenStaticLib/libtrdp.a)
```

# Build the static library yourself
1. Clone source repository: [TCNOpen](https://github.com/T12z/TCNopen).
2. `cd TCNopen/trdp/config`; Copy your needed configuration from `*_config` to `config.mk` and save.
3. `cd ..; make`
4. Find the generated static library from `trdp/bld/output`.
5. Put the `*.a` files and source code files into a folder as the target library to use.

# Resources
- [Protocol introduction](https://second.wiki/wiki/train_real_time_data_protocol)
- [TRDP Reference Manual](https://sourceforge.net/p/tcnopen/trdp/1564/tree/trunk/trdp/doc/TCN-TRDP2-D-BOM-033-xx%20-%20TRDP%20Reference%20Manual.pdf) 
