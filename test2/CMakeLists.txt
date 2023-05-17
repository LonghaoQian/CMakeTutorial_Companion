set(MyLibA_INCLUDE_DIR "")
set(MyLibA_LINK_DIR "")

add_subdirectory(third_party)

message(STATUS "lib_a include dir: " ${MyLibA_INCLUDE_DIR})
message(STATUS "lib_a link dir: " ${MyLibA_LINK_DIR})

add_executable(test2 test2.cpp)
target_link_libraries(test2 PUBLIC ${LASAN} MyLibA)
target_link_directories(test2 PUBLIC ${MyLibA_LINK_DIR})
target_compile_options(test2 PUBLIC ${GNU_FLAGS})
target_include_directories(test2 PUBLIC ${MyLibA_INCLUDE_DIR})