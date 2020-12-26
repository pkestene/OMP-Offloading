#
# Find Doxygen
#
find_package(Doxygen
  REQUIRED dot
  OPTIONAL_COMPONENTS mscgen dia)

if(NOT DOXYGEN_FOUND)

  message(WARNING "Doxygen need to be installed to generate the doxygen documentation. Can't go further.")

else()

set(DOC_SRC_DIR "${CMAKE_SOURCE_DIR}/docs")
set(DOC_BIN_DIR "${CMAKE_BINARY_DIR}/docs")
set(DOC_DEST_DIR "${CMAKE_BINARY_DIR}/docs/html")

set(DOXY_WARN_AS_ERR "NO")

set(DOXY_BUILD_HTML "YES")
set(DOXY_BUILD_XML "NO")
set(DOXY_OUTPUT_DIR "${DOC_DEST_DIR}")

configure_file(
  "${DOC_SRC_DIR}/Doxyfile.in"
  "${DOC_BIN_DIR}/Doxyfile"
  @ONLY)

add_custom_target(doc
  COMMAND Doxygen::doxygen "${DOC_BIN_DIR}/Doxyfile"
  COMMENT "Generating HTML API documentation with Doxygen")

add_custom_command(TARGET doc POST_BUILD
  COMMAND ;
  COMMENT "Output at ${DOC_DEST_DIR}/index.html")

add_custom_target(clean_doc
  COMMAND ${CMAKE_COMMAND} -E remove_directory "${DOC_DEST_DIR}")

endif()

