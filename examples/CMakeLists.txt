add_library(common STATIC common.cpp)
target_include_directories(common PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

add_library(common-ggml STATIC common-ggml.cpp)
target_link_libraries(common-ggml PRIVATE ggml)
target_include_directories(common-ggml PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

if (MSVC)
    target_compile_features(common PUBLIC cxx_std_20)
    target_compile_features(common-ggml PUBLIC cxx_std_20)
endif()

add_subdirectory(gpt-2)
add_subdirectory(gpt-j)
add_subdirectory(whisper)
add_subdirectory(mnist)
add_subdirectory(stablelm)
