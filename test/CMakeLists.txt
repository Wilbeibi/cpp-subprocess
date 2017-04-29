cmake_minimum_required(VERSION 3.1)

set (CMAKE_CXX_STANDARD 11)

include_directories("${CMAKE_CURRENT_SOURCE_DIR}/..")

file(GLOB TEST_SOURCES ./*.cc)

enable_testing() # make test or ctest to run all tests
foreach(testsourcefile ${TEST_SOURCES})
    get_filename_component(testname ${testsourcefile} NAME_WE)
    add_executable(${testname} ${testsourcefile})
    #target_link_libraries(${testname} ) # gtest
    add_test(NAME ${testname} COMMAND ${testname})
endforeach(testsourcefile ${TEST_SOURCES})