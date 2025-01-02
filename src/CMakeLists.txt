# link EasyX
# 设置包含目录
include_directories(${CMAKE_SOURCE_DIR}/extends/easyx/include)

# 导入静态库
add_library(EasyXa STATIC IMPORTED)
set_target_properties(EasyXa PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/extends/easyx/lib/EasyXa.lib)

add_library(EasyXw STATIC IMPORTED)
set_target_properties(EasyXw PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/extends/easyx/lib/EasyXw.lib)



add_executable(main main.cpp)

# link lib for main.exe
target_link_libraries(
    main
    PRIVATE
    EasyXa EasyXw
)

target_link_libraries(
    main
    PRIVATE
    module
)

add_subdirectory(module)