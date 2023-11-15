# CMakeList.txt: CMakeProject1 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#

if( CMAKE_BUILD_TYPE STREQUAL Debug)
	add_compile_definitions(DEBUG)
endif()

set(CMAKE_EXE_LINKER_FLAGS -static)

# 将源代码添加到此项目的可执行文件。
add_executable (tsh "tsh.c" "pel.c" "aes.c" "sha1.c")

add_compile_definitions(LINUX)
add_executable (tshd "tshd.c" "pel.c" "aes.c" "sha1.c")
target_link_libraries(tshd util)


if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET tsh PROPERTY CXX_STANDARD 20)
endif()

# TODO: 如有需要，请添加测试并安装目标。
