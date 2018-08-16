aux_source_directory (. SRC_LIST)

message(${SRC_LIST})

# add external libraries
find_package(OpenCV REQUIRED)
link_libraries(${PROJECT_SOURCE_DIR}/../FaceDetection/build/libseeta_facedet_lib.so)
link_libraries(${PROJECT_SOURCE_DIR}/../FaceAlignment/build/libseeta_fa_lib.so)

enable_testing ()
foreach (f ${SRC_LIST})
  string(REGEX REPLACE "[.]cpp" ".bin" BIN ${f})
  add_executable(${BIN} ${f})
  target_link_libraries(${BIN} viplnet ${OpenCV_LIBS})
endforeach ()

