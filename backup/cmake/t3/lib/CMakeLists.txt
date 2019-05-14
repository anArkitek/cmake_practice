set(LIBHELLO_SRC hello.c)

# on MacOS, it's ended by .dylib rather than .so
add_library(hello SHARED ${LIBHELLO_SRC})

# we can't use hello again because add_library() doesn't allow duplicate names
add_library(hello_static STATIC ${LIBHELLO_SRC})

# set the alias of hello_static to hello
set_target_properties(hello_static PROPERTIES OUTPUT_NAME "hello")

# don't clean previous outputs
set_target_properties(hello PROPERTIES CLEAN_DIRECT_OUTPUT 1)

set_target_properties(hello_static PROPERTIES CLEAN_DIRECT_OUTPUT 1)

# SOVERSION means API VERSION: different versions are not compatible each other
set_target_properties(hello PROPERTIES VERSION 1.2 SOVERSION 1)

# Example of GET_TARGET_PROPERTY
get_target_property(OUTPUT_VALUE hello_static OUTPUT_NAME)
message(STATUS "This is the thello_static OUTPUT_NAME: " ${OUTPUT_VALUE})

# install static & shared libraries
install(TARGETS hello hello_static 
    LIBRARY DESTINATION lib 
    ARCHIVE DESTINATION lib)

# install header file
install(FILES hello.h DESTINATION include/hello)