cmake_minimum_required(VERSION 3.10)
project(E01HelloWorld)

include_directories(
  ../capicxx-core-runtime/include
  ../capicxx-someip-runtime/include
  ../vsomeip/interface
  src-gen
)

link_directories(
  \${CMAKE_CURRENT_SOURCE_DIR}/../capicxx-core-runtime/build
  \${CMAKE_CURRENT_SOURCE_DIR}/../capicxx-someip-runtime/build
  \${CMAKE_CURRENT_SOURCE_DIR}/../vsomeip/build
)

add_executable(E01HelloWorldClient
  src/E01HelloWorldClient.cpp
  src-gen/v0/commonapi/examples/E01HelloWorldSomeIPProxy.cpp
  src-gen/v0/commonapi/examples/E01HelloWorldSomeIPDeployment.cpp
)

target_link_libraries(E01HelloWorldClient
  CommonAPI
  CommonAPI-SomeIP
  vsomeip3
)

add_executable(E01HelloWorldService
  src/E01HelloWorldService.cpp
  src/E01HelloWorldStubImpl.cpp
  src-gen/v0/commonapi/examples/E01HelloWorldSomeIPStubAdapter.cpp
  src-gen/v0/commonapi/examples/E01HelloWorldStubDefault.hpp
  src-gen/v0/commonapi/examples/E01HelloWorldSomeIPDeployment.cpp
)

target_link_libraries(E01HelloWorldService
  CommonAPI
  CommonAPI-SomeIP
  vsomeip3
)
