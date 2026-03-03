Manual Build Guide for Mankala Engine on Windows
This guide explains how to manually set up and build the Mankala Engine on Windows when automated tools like Craft are not functioning as expected. This process involves manual dependency management and specific workarounds for common build errors.

Prerequisites
Before starting, ensure you have the following installed and added to your system PATH:

MinGW-w64 (GCC): Version 14.x or higher is recommended.

CMake: Version 3.20 or higher.

7-Zip: For extracting dependency archives.

Step 1: Create a Root Directory
Create a dedicated folder to act as your library root (e.g., F:\Craft_Root). This folder will host all manually downloaded KDE frameworks and tools.

Step 2: Download and Install Dependencies
You need to manually download the binary packages for the required KDE Frameworks.

Extra CMake Modules (ECM):

Download the ECM binaries and extract them to F:\Craft_Root\share\ECM.

Ensure the cmake folder is present inside ECM.

Tier 1 Frameworks:

Download the .7z binary archives for ki18n, kconfig, and kcoreaddons from the KDE mirrors.

Extract each archive and merge their contents (bin, lib, include, share, plugins) into your F:\Craft_Root directory.

Note: When prompted by Windows, choose to "Replace/Merge" all existing folders.

Step 3: Clang-Tidy Workaround
During the build process, you might encounter an error regarding the -fno-keep-inline-dllexport argument. This is caused by a conflict between Clang-Tidy and the GCC compiler.

The Fix: Navigate to F:\Craft_Root\bin\ and rename clang-tidy.exe to clang-tidy.exe.bak. This prevents CMake from using the tool during compilation, bypassing the error.

Step 4: Configuring and Building
Open PowerShell in the root directory of the Mankala Engine source code and run the following commands:

PowerShell
# Create and enter the build directory
mkdir build
cd build

# Configure the project using CMake
# Pointing CMAKE_PREFIX_PATH to your root directory is crucial
F:\Craft_Root\dev-utils\bin\cmake.exe -G "MinGW Makefiles" -DCMAKE_PREFIX_PATH="F:\Craft_Root" ..

# Start the compilation process
F:\Craft_Root\mingw64\bin\mingw32-make.exe
Step 5: Running the Application
Once the build reaches 100%, your executable files will be located in the build/bin/ folder. To play the game, run:

PowerShell
cd bin
.\kalahtui.exe