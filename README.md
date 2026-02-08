# JUCE CMake Audio Plugin Template
## FINDSP additions for Linux

[![Build](https://img.shields.io/github/actions/workflow/status/anthonyalfimov/JUCE-CMake-Plugin-Template/Validation.yml?branch=main&logo=github)](https://github.com/anthonyalfimov/JUCE-CMake-Plugin-Template/actions)

A production-ready template for creating an audio plug-in using [JUCE 7/8](https://github.com/juce-framework/JUCE) and [CMake](https://cmake.org).

Designed as a **drop-in replacement for Projucer**, with clean, modern CMake workflows and zero required source changes.

See: **[Migrating from Projucer](MIGRATE_FROM_PROJUCER.md)**

---

## Features

- Drop-in replacement for Projucer (no source changes required)
- Can coexist alongside a `.jucer` project
- Generates clean:
  - Xcode
  - Visual Studio
  - Ninja / Make
- Minimal, organized project structure
- CMake manages dependencies automatically (JUCE shallow clone for faster downloads)
- GitHub Actions CI builds on macOS, Windows, and Linux
- Cached dependencies and compiler outputs for fast CI

---

## Generating IDE Projects

### macOS (Xcode)

```sh
cmake -B Build -G Xcode \
  -D CMAKE_OSX_ARCHITECTURES=arm64\;x86_64 \
  -D CMAKE_OSX_DEPLOYMENT_TARGET=10.15
````

Notes:

* `CMAKE_OSX_ARCHITECTURES=arm64\;x86_64` builds universal binaries (Apple Silicon + Intel)
* `CMAKE_OSX_DEPLOYMENT_TARGET=10.15` sets the minimum supported macOS version

---

### Windows (Visual Studio 2026)

```sh
cmake -B Build -G "Visual Studio 18 2026"
```

---

### Linux (Ninja)

```sh
cmake -B Build -G Ninja
```

### Ubuntu / Debian dependencies

```sh
sudo apt install build-essential cmake git \
  libasound2-dev libx11-dev libxrandr-dev libxinerama-dev \
  libxcursor-dev libxcomposite-dev libfreetype6-dev \
  libcurl4-openssl-dev libwebkit2gtk-4.0-dev
```

---

## Building

### Standard build

```sh
cmake --build Build --config Debug
```

### Using CMake Presets (recommended for Linux/macOS)

```sh
cmake --preset linux-release
cmake --build --preset linux-release
```

See `CMakePresets.json` for all available presets.

---

## Plugin Formats

| Platform | Formats              |
| -------- | -------------------- |
| Linux    | VST3, Standalone     |
| macOS    | AU, VST3, Standalone |
| Windows  | VST3, Standalone     |

Edit in:

```
CMakeLists.txt → juce_add_plugin() → FORMATS
```

---

## References

Based on:

* JUCE official example
  [https://github.com/juce-framework/JUCE/tree/master/examples/CMake/AudioPlugin](https://github.com/juce-framework/JUCE/tree/master/examples/CMake/AudioPlugin)

Inspired by:

* [https://github.com/sudara/pamplejuce](https://github.com/sudara/pamplejuce)
* [https://github.com/eyalamirmusic/JUCECmakeRepoPrototype](https://github.com/eyalamirmusic/JUCECmakeRepoPrototype)
* [https://github.com/findsp/JUCE-CMake-Plugin-Template](https://github.com/findsp/JUCE-CMake-Plugin-Template)

```


