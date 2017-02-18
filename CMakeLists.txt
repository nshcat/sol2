#########################
## sol2 CMake Project File
##

# Version requirement and project info
cmake_minimum_required(VERSION 3.1.3)
project(sol2)

# Define sol2 as header only interface.
# This used to carry the dependency on lua51
# into the parent target.
add_library(sol2 INTERFACE)

# Try to locate lua library
find_package(Lua 5.3 REQUIRED)

# Set dependencies as public
target_include_directories(sol2 INTERFACE ${LUA_INCLUDE_DIR} ${CMAKE_CURRENT_LIST_DIR}/include)
target_link_libraries(sol2 INTERFACE ${LUA_LIBRARIES})

# Set user variables
set(LIBSOL2_LIBRARIES sol2 CACHE INTERNAL "")
 