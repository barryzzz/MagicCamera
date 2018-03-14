# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)

# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds them for you.
# Gradle automatically packages shared libraries with your APK.

set(src_files
    src/main/jni/beautify/MagicBeautify.cpp
    src/main/jni/bitmap/BitmapOperation.cpp
    src/main/jni/bitmap/Conversion.cpp
    src/main/jni/MagicJni.cpp
)
add_library(MagicBeautify SHARED ${src_files})

find_library(log-lib
            log)
find_library( android-lib
              android )

target_link_libraries(MagicBeautify ${log-lib} ${android-lib} -ljnigraphics)