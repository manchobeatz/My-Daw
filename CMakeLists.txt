cmake_minimum_required(VERSION 3.22)

project(MANCHO_DAW VERSION 1.0.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include(FetchContent)

FetchContent_Declare(
    JUCE
    GIT_REPOSITORY https://github.com/juce-framework/JUCE.git
    GIT_TAG 8.0.6
)

FetchContent_MakeAvailable(JUCE)

juce_add_gui_app(MANCHO_DAW
    PRODUCT_NAME "MANCHO DAW"
)

target_sources(MANCHO_DAW
    PRIVATE
        Source/Main.cpp
)

target_compile_definitions(MANCHO_DAW
    PUBLIC
        JUCE_WEB_BROWSER=0
        JUCE_USE_CURL=0
)

target_link_libraries(MANCHO_DAW
    PRIVATE
        juce::juce_gui_extra
        juce::juce_audio_utils
)