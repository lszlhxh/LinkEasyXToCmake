# link EasyX
# 设置包含目录
include_directories(${CMAKE_SOURCE_DIR}/extends/easyx/include)

# 导入静态库 lib无需再编译生成
add_library(EasyXa STATIC IMPORTED)
add_library(EasyXw STATIC IMPORTED)
# 为 EasyXa 和 EasyXw 这两个量设置lib路径
set_target_properties(EasyXa PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/extends/easyx/lib/EasyXa.lib)
set_target_properties(EasyXw PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/extends/easyx/lib/EasyXw.lib)

# 生成可执行程序
add_executable(main main.cpp)

# link lib for main.exe
target_link_libraries(
    main
    PRIVATE
    EasyXa EasyXw
)

# 链接module的库，就是一个使用easyX的类
target_link_libraries(
    main
    PRIVATE
    module
)

#设置子目录
add_subdirectory(module)