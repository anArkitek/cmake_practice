CMAKE_MINIMUM_REQUIRED(VERSION 3.14)

# where we ADD_EXECUTABLE or ADD_LIBRARY where we place this command
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)
#SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/lib)

ADD_EXECUTABLE(hello main.c)

INSTALL(TARGETS hello RUNTIME DESTINATION bin)