#----------- find the installed package --------------#
message(STATUS "cmake install prefix: "  ${CMAKE_INSTALL_PREFIX})
find_package(TestLib CONFIG REQUIRED)
# check whether test lib is found
if(TestLib_FOUND)
    message(STATUS "TestLib found!")
    message(STATUS "TestLib include dir is: " ${TEST_LIB_INLCUDE_DIR}) # upper case (case sensitive)
    message(STATUS "TestLib library dir is: " ${TEST_LIB_LIBRARY_DIR})
else()
    message(STATUS "TestLib not found!")
endif()

#------------ compile a test target ------------------#
add_executable(test1 test1.cpp)
target_link_libraries(test1 PUBLIC ${LASAN} MyLibB)
target_link_directories(test1 PUBLIC ${TEST_LIB_LIBRARY_DIR})
target_compile_options(test1 PUBLIC ${GNU_FLAGS})
target_include_directories(test1 PUBLIC ${TEST_LIB_INLCUDE_DIR})