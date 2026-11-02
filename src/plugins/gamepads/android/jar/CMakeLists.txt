# Generated from jar.pro.

if(COMMAND qt_get_android_sdk_jar_for_api)
    qt_get_android_sdk_jar_for_api("android-16" android_sdk)
elseif(EXISTS "${QT_ANDROID_JAR}")
    # Qt 6.12 removed the helper; use the SDK selected by Qt's Android toolchain.
    set(android_sdk "${QT_ANDROID_JAR}")
else()
    message(FATAL_ERROR "Cannot find android.jar; check the Android SDK configuration.")
endif()

set(java_sources
    src/org/qtproject/qt/android/gamepad/QtGamepad.java
)

qt_internal_add_jar(QtAndroidGamepad
    INCLUDE_JARS ${android_sdk}
    SOURCES ${java_sources}
    OUTPUT_DIR "${QT_BUILD_DIR}/jar"
)

install_jar(QtAndroidGamepad
    DESTINATION jar
    COMPONENT Devel
)

