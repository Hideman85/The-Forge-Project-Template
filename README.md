# The-Forge-Project-Template

Just a simple project template for quick start using The-Forge.

Keep in mind The-Forge **is not** a game engine but a **rendering framework** and it's up to you to build your own engine on top of this.

## Cloning

This project use [git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) feature so you must clone the repo recursively
```bash
git clone --recursive https://github.com/Hideman85/The-Forge-Project-Template.git MyAwesomeProject
```

## Building

This project use CMake as build engine and if you need to use it in a IDE that not support CMake look at [CMake Generators](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html).

CMake allow a easy way to crosscompile the code for all targets on the same machine via [Toolchains](https://cmake.org/cmake/help/latest/manual/cmake-toolchains.7.html).

And finally you can use a collection of [docker containers](https://www.docker.com/resources/what-container) for easily crosscompile with pre-setup environments thanks to [dockcross](https://github.com/dockcross/dockcross).

### Building on linux

```bash
cd MyAwesomeProject
mkdir -p build/Linux
cd build/Linux
cmake ../..
make -j$(nproc)
```

#### Crosscompiling

- Pull docker image
```bash
docker pull dockcross/windows-static-x64
docker run dockcross/windows-static-x64 > Scripts/MingW64Compilation
chmod +x Scripts/MingW64Compilation
```

- Open a terminal in the container environment
```bash
./Scripts/MingW64Compilation bash
mkdir -p build/MingW64
cmake ../..
make -j$(nproc)
```

## Some extra libs

- [YAS](https://github.com/niXman/yas) - Yet Another Serialization is a very fast, cross-platform, endian independent and header only serialization library.
