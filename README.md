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

    depends: nanoflann ^1.5.4

The library can be imported by the following declaration in a `buildfile`.

    import nanoflann = nanoflann%lib{nanoflann}

## Configuration
There are no configuration options available.

## Issues
- `freebsd_13-clang_14.0-static_O3` error (test-installed):
    + `ld: error: undefined symbol: pthread_create`
    + It seems that `pthread` is not correctly linked in the examples.
- `linux_debian_11-emcc_3.1.6` error (test):
    + `em++` seems not to be able to compile `gtest`.

## Contributing
Thanks in advance for your help and contribution to keep this package up-to-date.
For now, please, file an issue on [GitHub](https://github.com/build2-packaging/nanoflann/issues) for everything that is not described below.

### Recommend Updating Version
Please, file an issue on [GitHub](https://github.com/build2-packaging/nanoflann/issues) with the new recommended version.

### Update Version by Pull Request
1. Fork the repository on [GitHub](https://github.com/build2-packaging/nanoflann) and clone it to your local machine.
2. Run `git submodule init` and `git submodule update` to get the current upstream directory.
3. Inside the `upstream` directory, checkout the new library version `X.Y.Z` by calling `git checkout vX.Y.Z` that you want to be packaged.
4. If needed, change source files, `buildfiles`, and symbolic links accordingly to create a working build2 package. Make sure not to directly depend on the upstream directory inside the build system but use symbolic links instead.
5. Update library version in `manifest` file if it has changed or add package update by using `+n` for the `n`-th update.
6. Make an appropriate commit message by using imperative mood and a capital letter at the start and push the new commit to the `master` branch.
7. Run `bdep ci` and test for errors.
8. If everything works fine, make a pull request on GitHub and write down the `bdep ci` link to your CI tests.
9. After a successful pull request, we will run the appropriate commands to publish a new package version.

### Update Version Directly if You Have Permissions
1. Inside the `upstream` directory, checkout the new library version `X.Y.Z` by calling `git checkout vX.Y.Z` that you want to be packaged.
2. If needed, change source files, `buildfiles`, and symbolic links accordingly to create a working build2 package. Make sure not to directly depend on the upstream directory inside the build system but use symbolic links instead.
3. Update library version in `manifest` file if it has changed or add package update by using `+n` for the `n`-th update.
4. Make an appropriate commit message by using imperative mood and a capital letter at the start and push the new commit to the `master` branch.
5. Run `bdep ci` and test for errors and warnings.
6. When successful, run `bdep release --tag --push` to push new tag version to repository.
7. Run `bdep publish` to publish the package to [cppget.org](https://cppget.org).
