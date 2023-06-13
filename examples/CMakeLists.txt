project(libaffa-examples LANGUAGES CXX)

# For now, only support example1 and example2, because
# I cannot find the libEasyVal for download.
foreach(executable example1;example2)
    add_executable(${executable} ${executable}.cpp)
    target_compile_features(${executable} PRIVATE cxx_std_20)
    target_link_libraries(${executable} PRIVATE libaffa::libaffa)
    set_target_properties(${executable} PROPERTIES CXX_EXTENSIONS OFF)
endforeach()