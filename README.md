Mankala Engine - Manual Windows Build
This repository contains a successful manual build of the KDE Mankala Engine on Windows. Due to issues with automated setup tools, this project was built by manually managing dependencies and resolving compiler conflicts.

🚀 Key Achievements:
Manual Dependency Management: Successfully integrated ECM, ki18n, kconfig, and kcoreaddons into a custom root directory.

Build Optimization: Resolved the Clang-Tidy and GCC conflict that was halting the build at 9%.

Full Compilation: Achieved a 100% successful build of the engine and TUI examples.

📄 Documentation
For a detailed, step-by-step guide on how I resolved these issues and built the project, please check:
👉 SETUP_WINDOWS.md

🎮 How to Play
The compiled executables can be found in the build/bin folder.

PowerShell
.\kalahtui.exe
