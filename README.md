# CPP

A starting point for new C++ projects. Create a repository from it with
**Use this template** on GitHub, then rename the project.

## What's included

- `CMakeLists.txt`: a single executable target built as C++20 with
  extensions off. Warnings are strict (`-Wall -Wextra -Wpedantic -Wconversion
  -Wsign-conversion` on Clang/GCC, `/W4` on MSVC) and treated as errors unless
  `WARNINGS_AS_ERRORS` is turned off.
- `CMakePresets.json`: Debug and Release presets for Clang + Ninja on Windows.
  Builds go to `build/<preset>/`.
- `.clangd`: strict missing/unused include diagnostics.
- `.vscode/`: a default build task through the CMake Tools extension and an
  LLDB launch configuration for the active target.

## Using it

1. Replace `cpp` with your project name in `CMakeLists.txt` (the `project()`
   call and the target name).
2. Configure and build:

   ```bash
   cmake --preset windows-clang-debug
   cmake --build --preset windows-clang-debug
   ```

On Linux or macOS, add presets for your toolchain; the existing ones only
apply on Windows hosts.

## Requirements

- CMake 4.0+
- Ninja
- Clang (`clang++` on `PATH`)
