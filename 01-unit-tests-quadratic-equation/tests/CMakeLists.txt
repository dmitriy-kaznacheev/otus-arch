include(FetchContent)

option(BUILD_GMOCK OFF)
option(INSTALL_GTEST OFF)

FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG        release-1.11.0
)

FetchContent_MakeAvailable(googletest)

add_library(
  GTest::GTest 
  INTERFACE 
  IMPORTED
)
target_link_libraries(
  GTest::GTest 
  INTERFACE 
  gtest_main
)

add_executable(
  quad_equation_test 
  quad_equation_test.cpp
)

target_link_libraries(quad_equation_test
  PRIVATE
  GTest::GTest
  quad_equation
)

add_test(
  01_quad_equation_gtest 
  quad_equation_test
)
