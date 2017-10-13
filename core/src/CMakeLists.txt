
TRIBITS_ADD_OPTION_AND_DEFINE(
  Kokkos_ENABLE_Serial
  KOKKOS_HAVE_SERIAL
  "Whether to enable the Kokkos::Serial device.  This device executes \"parallel\" kernels sequentially on a single CPU thread.  It is enabled by default.  If you disable this device, please enable at least one other CPU device, such as Kokkos::OpenMP or Kokkos::Threads."
  ON
  )

ASSERT_DEFINED(${PROJECT_NAME}_ENABLE_CXX11)
ASSERT_DEFINED(${PACKAGE_NAME}_ENABLE_CUDA)

TRIBITS_CONFIGURE_FILE(${PACKAGE_NAME}_config.h)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR})
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})

FILE(GLOB_RECURSIVE soruces *.cpp)

TRIBITS_ADD_LIBRARY(
    kokkoscore
    SOURCES ${SOURCES}
    DEPLIBS
    )

TRIBITS_INSTALL_HEADERS(
  SOURCE_BASE_DIR ${CMAK_CURRENT_SORUCE_DIR}
  FILES_MATCHING PATTERN "*.hpp"
  )
