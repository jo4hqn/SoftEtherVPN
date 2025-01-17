How to build SoftEther VPN for Windows
======================================

There are several methods for using CMake but the easiest by far is through Visual Studio by importing the CMake project directly
into it. So that is what will be described below.

## Requirements

- Visual Studio 2019 or 2022 (Community Edition is fine)

  https://visualstudio.microsoft.com/downloads

- Git for Windows (or other git tool)

  https://gitforwindows.org/

- vcpkg

  https://github.com/microsoft/vcpkg

## Installation

- Visual Studio

  Download from the official site and run the installer.

  Make sure to check **Desktop development with C++** under *Workloads* and **Clang C++ Tools for Windows** in *Optional* components.

- Git

  Nothing special. Just follow the installer.

- vcpkg

  Let's say you will install it to `C:\vcpkg`.

  Open your preferred terminal and go to `C:\`. Then run these commands.

  ```
  C:\> git clone https://github.com/microsoft/vcpkg
  C:\> cd vcpkg
  C:\vcpkg> bootstrap-vcpkg.bat
  C:\vcpkg> vcpkg integrate install
  ```

## Building

1. Launch Visual Studio

   Choose either **Clone a repository** to clone from GitHub or **Open a local folder** if you already have a copy.

1. Open Terminal (*View -> Terminal*). Install the needed submodules to build the project, avoiding CMake telling you to do so with:

   `git submodule update --init --recursive`

   **Note**: This step is not necessary if you have chosen **Clone a repository** as Visual Studio automatically takes care of it.

1. Select a configuration from the dropdown menu below the search box. The default configurations are:

   - x64-native

     Build x64 executables with 64-bit compiler (most common)

   - x64-on-x86

     Cross compile x64 executables with 32-bit compiler

   - x86-native

     Build x86 executables with 32-bit compiler

   - x86-on-x64

     Cross compile x86 executables with 64-bit compiler

   On 64-bit Windows, all four configurations can be used. 32-bit platforms can only use 32-bit compiler.

1. Visual Studio will try generating CMake cache. If not, click **Project -> Configure Cache** or **Generate Cache**.

   If CMake is busy, you will find **Generate Cache** greyed out. Wait until it finishes or click **Cancel CMake Cache Generation** to stop it.

   The initial configuration will take a longer time since it needs to download and install dependencies.

1. When *CMake generation finished* is displayed, simply go to toolbar and click **Build -> Build All**.

1. Once building has finished, hopefully with no errors, look in the newly created `/build` directory in the project's folder.

   Run `vpnsetup.exe` to install desired components.

1. Congrats, you now have a complete CMake development environment for SoftEtherVPN on Windows, enjoy and happy contributing!
