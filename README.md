# ubuntu-cmake-clang

Docker image of various cmake and clang.

## Docker tags

Each folder name is the same as the docker tag.

## Simple Usage
For example, to build a CMake-based project into `build` with cmake 3.13.5 and clang 6.0.0, type:
```sh
docker run --rm \
  -v $(pwd):/usr/src/myapp \
  -w=/usr/src/myapp developmaso/ubuntu-cmake-clang:cmake3.13.5-clang6.0.0 \
  /bin/bash -c "mkdir build && cd build && cmake .. && make"
```
