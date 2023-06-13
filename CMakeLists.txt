cmake_minimum_required(VERSION 3.25)
project(libaffa LANGUAGES CXX)

set(libaffa_header_files
    src/aa_aaf.h
    src/aa_interval.h
    src/aa_rounding.h
    src/aa_util.h
    src/aa.h
)

set(libaffa_source_files
    src/aa_aafapprox.cpp
    src/aa_aafarithm.cpp
    src/aa_aafcommon.cpp
    src/aa_aaftrigo.cpp
    src/aa_interval.cpp
    src/aa_rounding.cpp
)

add_library(libaffa_libaffa STATIC ${libaffa_header_files} ${libaffa_source_files})
target_include_directories(libaffa_libaffa PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/src/)
target_compile_features(libaffa_libaffa PRIVATE cxx_std_20)
set_target_properties(libaffa_libaffa PROPERTIES CXX_EXTENSIONS OFF)

# Despite being good practice, the "warning as errors" flag will make your compiler scream in agony.
# Lets postpone this for future refinement.
#if (MSVC)
#    target_compile_options(libaffa_libaffa PRIVATE /W4 /WX)
#elseif()
#    target_compile_options(libaffa_libaffa PRIVATE -Wall -Wextra -Wpedantic)
#endif()

add_library(libaffa::libaffa ALIAS libaffa_libaffa)

add_subdirectory(examples)