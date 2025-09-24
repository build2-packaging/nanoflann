# nanoflann - C++ Library for Nearest Neighbor Search with KD-Trees

This is the `build2` package for nanoflann, a C++11 header-only library for Nearest Neighbor (NN) search with KD-trees.

# Usage
To use `nanoflann` in your project, add the following configurations to the respective files after you have gained access to a `build2` package repository that contains it.

### `manifest`
To make `nanoflann` available for import, add the following dependency to the `manifest` of each package in your project that requires it, adjusting the version constraint as appropriate.

    depends: nanoflann ^1.7.1

### `buildfile`
To import the contained library, use the following declaration in your `buildfile`.

    import nanoflann = nanoflann%lib{nanoflann}

### C++ Header Inclusion
Finally, include the nanoflann header in your C++ source code.

```c++
#include <nanoflann.hpp>
```
