# build2 Package for nanoflann

This project builds and defines the build2 package for [nanoflann](https://github.com/jlblancoc/nanoflann), a C++11 header-only library for Nearest Neighbor (NN) search with KD-trees.

[![Official](https://img.shields.io/website/https/github.com/jlblancoc/nanoflann.svg?down_message=offline&label=Official&style=for-the-badge&up_color=blue&up_message=online)](https://github.com/jlblancoc/nanoflann)
[![build2](https://img.shields.io/website/https/github.com/build2-packaging/nanoflann.svg?down_message=offline&label=build2&style=for-the-badge&up_color=blue&up_message=online)](https://github.com/build2-packaging/nanoflann)
[![cppget.org](https://img.shields.io/website/https/cppget.org/nanoflann.svg?down_message=offline&label=cppget.org&style=for-the-badge&up_color=blue&up_message=online)](https://cppget.org/nanoflann)
[![queue.cppget.org](https://img.shields.io/website/https/queue.cppget.org/nanoflann.svg?down_message=empty&down_color=blue&label=queue.cppget.org&style=for-the-badge&up_color=orange&up_message=running)](https://queue.cppget.org/nanoflann)

## Usage
Make sure to add the stable section of the `cppget.org` repository to your project's `repositories.manifest` to be able to fetch the package.

    :
    role: prerequisite
    location: https://pkg.cppget.org/1/stable
    # trust: ...

If the stable section of `cppget.org` is not an option then add this Git repository itself instead as a prerequisite.

    :
    role: prerequisite
    location: https://github.com/build2-packaging/nanoflann.git

Add the respective dependency in your project's `manifest` file to make the package available for import.

    depends: nanoflann ^1.6.0

The library can be imported by the following declaration in a `buildfile`.

    import nanoflann = nanoflann%lib{nanoflann}

## Configuration
There are no configuration options available.

## Issues
- FreeBSD, Clang, static, optimized: Error may occur during tests or installed tests:
    + `ld: error: undefined symbol: pthread_create`
    + It seems that `pthread` is not correctly linked in the examples.
- `linux_debian_11-emcc_3.1.6` error (test):
    + `em++` seems not to be able to compile `gtest`.
- Windows, MinGW, optimized: The `kdtree.SO2_vs_bruteforce` test may fail.

## Contributing
Thank you in advance for your help and contribution to keep this package up-to-date.
Please, file an issue on [GitHub](https://github.com/build2-packaging/nanoflann/issues) for questions, bug reports, or to recommend updating the package version.
If you're making a pull request to fix bugs or update the package version yourself, refer to the [`build2` Packaging Guidelines](https://build2.org/build2-toolchain/doc/build2-toolchain-packaging.xhtml#core-version-management).
