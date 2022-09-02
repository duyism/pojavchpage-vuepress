# Getting PojavLauncher from source


## *PojavLauncher can be built from source on Linux. If you're on Windows, you can use WSL or Cygwin.*

## Prerequisites

To build PojavLauncher itself you'll need only `openjdk-8-jdk` or higher package installed.  
Building gl4es requires Android NDK (optional).

## Building

1. Clone the repository:  
`git clone https://github.com/PojavLauncherTeam/PojavLauncher`

2. Update translations:  
`cd PojavLauncher && chmod +x scripts/languagelist_updater.sh && bash scripts/languagelist_updater.sh`

3. Get and build gl4es fork (optional):  
`git clone https://github.com/PojavLauncherTeam/gl4es && cd gl4es && $ANDROID_NDK_HOME/ndk-build NDK_PROJECT_PATH=. APP_BUILD_SCRIPT=./Android.mk NDK_DEBUG=1 && cp -R libs/* app_pojavlauncher/src/main/jniLibs/ && cd ..`

4. Get JRE:  
Download `jre8-pojav` artifact from [autobuilds](https://github.com/PojavLauncherTeam/android-openjdk-build-multiarch/actions?query=is%3Asuccess+branch%3Abuildjre8) and unpack it's contents into `app_pojavlauncher/src/main/assets/components/jre` directory.

5. Build & install GLFW:  
`mkdir -p out && chmod +x gradlew && ./gradlew clean && ./gradlew :jre_lwjgl3glfw:build && rm app_pojavlauncher/src/main/assets/components/lwjgl3/lwjgl-glfw-classes.jar && cp jre_lwjgl3glfw/build/libs/jre_lwjgl3glfw-3.2.3.jar app_pojavlauncher/src/main/assets/components/lwjgl3/lwjgl-glfw-classes.jar`

6. Build the launcher:  
`./gradlew :app_pojavlauncher:assembleDebug && mv app_pojavlauncher/build/outputs/apk/debug/app_pojavlauncher-debug.apk out/app-debug.apk`

You should now have a new .apk file sitting in `out` directory. Go ahead and install this on your device and you're all good to go!
