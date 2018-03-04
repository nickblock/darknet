

cmake_minimum_required(VERSION 2.8)

if( ANDROID_ABI )
  if(${ANDROID_ABI} STREQUAL "armeabi-v7a")
      include_directories(${ANDROID_SYSROOT}/usr/include/arm-linux-androideabi)
  elseif(${ANDROID_ABI} STREQUAL "arm64-v8a")
      include_directories(${ANDROID_SYSROOT}/usr/include/aarch64-linux-android)
  else()
      include_directories(${ANDROID_SYSROOT}/usr/include/arm-linux-androideabi)
  endif()
  set(CMAKE_C_FLAGS "-include ${CINDER_DIR}/include/cinder/app/android/android_fopen.h")
endif()


if( "" STREQUAL "${CMAKE_BUILD_TYPE}" )
    set( CMAKE_BUILD_TYPE "Debug" CACHE FILEPATH "" FORCE )
endif()
if( "Debug" STREQUAL "${CMAKE_BUILD_TYPE}" )
    set( CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -g" )
endif()


add_library(darknet 
  src/gemm.c
  src/utils.c
  src/cuda.c
  src/deconvolutional_layer.c
  src/convolutional_layer.c
  src/list.c
  src/image.c
  src/activations.c
  src/im2col.c
  src/col2im.c
  src/blas.c
  src/crop_layer.c
  src/dropout_layer.c
  src/maxpool_layer.c
  src/softmax_layer.c
  src/data.c
  src/matrix.c
  src/network.c
  src/connected_layer.c
  src/cost_layer.c
  src/parser.c
  src/option_list.c
  src/detection_layer.c
  src/route_layer.c
  src/box.c
  src/normalization_layer.c
  src/avgpool_layer.c
  src/layer.c
  src/local_layer.c
  src/shortcut_layer.c
  src/activation_layer.c
  src/rnn_layer.c
  src/gru_layer.c
  src/crnn_layer.c
  src/demo.c
  src/batchnorm_layer.c
  src/region_layer.c
  src/reorg_layer.c
  src/tree.c
  src/lstm_layer.c
  src/option_list.c
)

target_include_directories( darknet PRIVATE 
  include
)
