# Distributed under the MIT License.
# See LICENSE.txt for details.

set(LIBRARY Evolution)

set(LIBRARY_SOURCES
  Initialization/DgDomain.cpp
  TagsDomain.cpp
  )

add_spectre_library(${LIBRARY} ${LIBRARY_SOURCES})

target_link_libraries(
  ${LIBRARY}
  PUBLIC
  Boost::boost
  Domain
  DataStructures
  Options
  Utilities

  PRIVATE
  LinearOperators
  )

add_dependencies(
  ${LIBRARY}
  module_ConstGlobalCache
  )

add_subdirectory(DiscontinuousGalerkin)
add_subdirectory(Executables)
add_subdirectory(Systems)
add_subdirectory(VariableFixing)
