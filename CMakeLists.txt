cmake_minimum_required (VERSION 2.8)
project (attackiq-dnp3-client)
set(ATTACKIQ_DNP3_CLIENT_VERSION 1.0.0)

# other options off-by-default that you can enable
option(WERROR "Set all warnings to errors" OFF)
option(STATICLIBS "Builds static versions of all installed libraries" OFF)
option(COVERAGE "Builds the libraries with coverage info for gcov" OFF)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wno-parentheses --std=c++11")
set(OPENDNP3_LIBRARIES asiodnp3 opendnp3 asiopal openpal)

include_directories(./tclap/include)

# ----- client executable -----
file(GLOB_RECURSE dnp3-master_SRC ./src/client/*.cpp ./src/client/*.h)
add_executable(dnp3-master ${dnp3-master_SRC})
target_link_libraries (dnp3-master LINK_PUBLIC ${OPENDNP3_LIBRARIES} pthread)
