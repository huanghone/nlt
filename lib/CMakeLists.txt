cmake_minimum_required(VERSION 3.12)
project(libs)

include(ExternalProject)

set(glm_PREFIX "${CMAKE_SOURCE_DIR}/glm")
ExternalProject_Add( glm
  GIT_REPOSITORY https://gitee.com/huanghone/glm.git
  GIT_TAG 0.9.3.4
  CMAKE_ARGS 
    -DCMAKE_INSTALL_PREFIX=${glm_PREFIX}
    -DCMAKE_BUILD_TYPE=Release
    -DBUILD_SHARED_LIBS=ON
    -DBUILD_STATIC_LIBS=ON
    -DGLM_TEST_ENABLE=ON
)

set(glew_PREFIX "${CMAKE_SOURCE_DIR}/glew")
ExternalProject_Add( glew
  GIT_REPOSITORY https://github.com/Perlmint/glew-cmake.git
  GIT_TAG glew-cmake-2.2.0
  CMAKE_ARGS 
    -DCMAKE_INSTALL_PREFIX=${glew_PREFIX}
    -DCMAKE_BUILD_TYPE=Release
    -DONLY_LIBS=ON
    -Dglew-cmake_BUILD_SHARED=ON
    -Dglew-cmake_BUILD_STATIC=OFF
)

set(glfw_PREFIX "${CMAKE_SOURCE_DIR}/glfw")
ExternalProject_Add( glfw
  GIT_REPOSITORY https://gitee.com/huanghone/glfw.git
  GIT_TAG 3.3.8
  CMAKE_ARGS 
    -DCMAKE_INSTALL_PREFIX=${glfw_PREFIX}
    -DCMAKE_BUILD_TYPE=Release
    -DBUILD_SHARED_LIBS=ON
    -DGLFW_BUILD_DOCS=OFF
    -DGLFW_BUILD_EXAMPLES=OFF
    -DGLFW_BUILD_TESTS=OFF
    -DGLFW_INSTALL=ON
)

set(assimp_PREFIX "${CMAKE_SOURCE_DIR}/assimp")
ExternalProject_Add( assimp
  PREFIX "${assimp_PREFIX}"
  GIT_REPOSITORY https://gitee.com/huanghone/assimp.git
  GIT_TAG v3.3.1
  #SOURCE_DIR ${CMAKE_SOURCE_DIR}/assimp-3.3.1
  #URL "D:/code/nonlocal-tracker/lib/assimp/src/assimp-3.3.1.zip"
  #DOWNLOAD_NAME assimp-3.3.1.zip
  CMAKE_ARGS 
    -DCMAKE_INSTALL_PREFIX=${assimp_PREFIX}
    -DCMAKE_BUILD_TYPE=Release
    -DINJECT_DEBUG_POSTFIX=OFF
    -DASSIMP_BUILD_TESTS=OFF
    -DASSIMP_BUILD_ASSIMP_TOOLS=OFF
    -DASSIMP_BUILD_ZLIB=OFF
)

set(opencv_PREFIX "${CMAKE_SOURCE_DIR}/opencv")
ExternalProject_Add( opencv
  GIT_REPOSITORY https://gitee.com/mirrors/opencv.git
  GIT_TAG 3.4.18
  INSTALL_DIR ${opencv_PREFIX}
  CMAKE_ARGS
    -DCMAKE_INSTALL_PREFIX=${opencv_PREFIX}
    -DCMAKE_BUILD_TYPE=Release
    -DBUILD_SHARED_LIBS=ON
    -DWITH_IPP=OFF
    -DWITH_OPENGL=ON
    -DBUILD_opencv_js=OFF
    -DBUILD_IPP_IW=OFF
    -DBUILD_JAVA=OFF
    -DBUILD_openv_apps=OFF
    -DBUILD_opencv_dnn=OFF
    -DBUILD_opencv_objdetect=OFF
    -DBUILD_opencv_superres=OFF
    -DBUILD_opencv_flann=ON
    -DBUILD_opencv_stitching=OFF
    -DBUILD_opencv_shape=OFF
    -DBUILD_opencv_ml=OFF
    -DBUILD_opencv_photo=OFF
    -DBUILD_opencv_videostab=OFF
    -DBUILD_opencv_java_bindings_generator=OFF
    -DBUILD_opencv_python_bindings_generator=OFF
    -DBUILD_opencv_python_tests=OFF
    -DBUILD_opencv_js_bindings_generator=OFF
    -DBUILD_opencv_ts=OFF
    -DBUILD_PERF_TEST=OFF
    -DBUILD_TEST=OFF
    -DINSTALL_PDB=OFF
    -DINSTALL_PDB_COMPONENT_EXCLUDE_FROM_ALL=OFF
)
