# build2 Package Repository for nanoflann

This is a [build2](https://build2.org) package repository for [nanoflann](https://github.com/jlblancoc/nanoflann), a C++11 header-only library for Nearest Neighbor (NN) search with KD-trees.

This repository is a community-maintained effort and is not officially endorsed by the nanoflann authors.

| Package | Summary | Status |
|---|---|---|
| **[`nanoflann`](nanoflann/PACKAGE-README.md)** | C++ NN-Search/KD-Trees Library | [![cppget.org](https://img.shields.io/website/https/cppget.org/nanoflann.svg?down_message=offline&label=cppget.org&style=for-the-badge&up_color=blue&up_message=online)](https://cppget.org/nanoflann) [![queue.cppget.org](https://img.shields.io/website/https/queue.cppget.org/nanoflann.svg?down_message=empty&down_color=blue&label=queue.cppget.org&style=for-the-badge&up_color=orange&up_message=running)](https://queue.cppget.org/nanoflann) |

## Usage
If you want to use the `nanoflann` package in your `build2`-based project, add an appropriate repository manifest to your project's `repositories.manifest` and refer to [`nanoflann`'s PACKAGE README](nanoflann/PACKAGE-README.md).

### `repositories.manifest`
To be able to fetch the package, add one of the following prerequisites to your project's `repositories.manifest`.

**Option A: `cppget.org` (Recommended)**

Based on your project's stability requirements, choose either the [`stable` section](https://cppget.org/?about#pkg%3Acppget.org%2Fstable) for thoroughly tested versions or the [`testing` section](https://cppget.org/?about#pkg%3Acppget.org%2Ftesting) for the latest releases before they are marked as stable.
For example:

    :
    role: prerequisite
    location: https://pkg.cppget.org/1/stable
    # trust: ...

**Option B: Git Repository**

    :
    role: prerequisite
    location: https://github.com/build2-packaging/nanoflann.git

## Development Setup
The development setup for this repository uses the standard `bdep`-based workflow.
For general information and guidance on package maintenance, please see the [`build2` Documentation](https://build2.org/doc.xhtml).

First, clone the repository via SSH or HTTPS.

    git clone --recurse https://github.com/build2-packaging/nanoflann.git  # HTTPS
    git clone --recurse git@github.com:build2-packaging/nanoflann.git      # SSH

Inside the repository's directory, initialize your build configuration.

    bdep init -C @gcc cc config.cxx=g++ config.install.root=../.install config.dist.root=../.dist

Afterwards, use `b` or `bdep` to build, test, install, and distribute the packages.

## Issues
- FreeBSD, Clang, static, optimized: Error may occur during tests or installed tests:
    + `ld: error: undefined symbol: pthread_create`
    + It seems that `pthread` is not correctly linked in the examples.
- `linux_debian_11-emcc_3.1.6` error (test):
    + `em++` seems not to be able to compile `gtest`.
- Windows, MinGW, optimized: The `kdtree.SO2_vs_bruteforce` test may fail.

## Contributing
Contributions are welcome and greatly appreciated!
Please start by [opening an issue](https://github.com/build2-packaging/nanoflann/issues) to report a bug, suggest an improvement, or request a version update.
This helps us coordinate efforts and avoid duplicate work.
You are then welcome to submit a [pull request](https://github.com/build2-packaging/nanoflann/pulls) that references the issue.
For guidance on package maintenance, please see the [`build2` Packaging Guidelines](https://build2.org/build2-toolchain/doc/build2-toolchain-packaging.xhtml).
