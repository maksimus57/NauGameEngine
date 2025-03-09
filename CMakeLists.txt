cmake_minimum_required (VERSION 3.30.1)

project(NauGameEngine
    VERSION 1.0.0
    DESCRIPTION "Nau Game Engine complete project"
    LANGUAGES C CXX
)

# Options
option(NAU_ENGINE_BUILD "Build Nau Engine" ON)
option(NAU_EDITOR_BUILD "Build Nau Editor" ON)
option(NAU_AS_BUILD "Build Nau Agnostic Scripting project" OFF)

# Dependencies
if(NAU_ENGINE_BUILD)
    list(APPEND VCPKG_MANIFEST_FEATURES "build-nau-engine")
endif(NAU_ENGINE_BUILD)
if(NAU_EDITOR_BUILD)
    # Check if Nau Engine Build
    list(APPEND VCPKG_MANIFEST_FEATURES "build-nau-editor")
endif(NAU_EDITOR_BUILD)
if(NAU_AS_BUILD)
    list(APPEND VCPKG_MANIFEST_FEATURES "build-nau-as")
endif(NAU_AS_BUILD)

# Subprojects
if(NAU_ENGINE_BUILD)
    add_subdirectory(NauEngine)
endif(NAU_ENGINE_BUILD)
if(NAU_EDITOR_BUILD)
    # Check if Nau Engine Build
    add_subdirectory(NauEditor)
endif(NAU_EDITOR_BUILD)
if(NAU_AS_BUILD)
    add_subdirectory(NauAS)
endif(NAU_AS_BUILD)