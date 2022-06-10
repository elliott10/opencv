## OpenCV: Open Source Computer Vision Library
---
### Cross compilation for riscv64 with musl libc
#### Install cross compilation tools:
```
wget https://musl.cc/riscv64-linux-musl-cross.tgz
tar xvf riscv64-linux-musl-cross.tgz
export PATH=/path/to/riscv64-linux-musl-cross/bin:$PATH
```

#### Building dependency FFMPEG
```
cd ffmpeg-5.0.1
mkdir build
./configure --enable-cross-compile --cross-prefix=riscv64-linux-musl- --arch=riscv64 --target-os=linux --enable-static --enable-shared --prefix=$PWD/install \

make
make install
```


#### Getting and Building OpenCV Source Code

```
git clone https://github.com/elliott10/opencv.git

mkdir -p opencv/build && cd opencv/build
export PKG_CONFIG_LIBDIR=/path/to/ffmpeg-5.0.1/build/install/lib/pkgconfig

cmake -DCMAKE_TOOLCHAIN_FILE=../platforms/linux/riscv64-musl-gcc.toolchain.cmake -DWITH_FFMPEG=ON -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=$PWD/install  ../

make -j8
make install
```
Notice:
<br> When runing cmake, please remember to set `PKG_CONFIG_LIBDIR`.
<br> After cmake, make sure the output is like this:
```
FFMPEG:                      YES
  avcodec:                   YES
  avformat:                  YES
  avutil:                    YES
  swscale:                   YES
```
The compiled binaries will be placed in this directory: `opencv/build/bin/`

---
### Resources

* Homepage: <https://opencv.org>
  * Courses: <https://opencv.org/courses>
* Docs: <https://docs.opencv.org/4.x/>
* Q&A forum: <https://forum.opencv.org>
  * previous forum (read only): <http://answers.opencv.org>
* Issue tracking: <https://github.com/opencv/opencv/issues>
* Additional OpenCV functionality: <https://github.com/opencv/opencv_contrib> 


### Contributing

Please read the [contribution guidelines](https://github.com/opencv/opencv/wiki/How_to_contribute) before starting work on a pull request.

#### Summary of the guidelines:

* One pull request per issue;
* Choose the right base branch;
* Include tests and documentation;
* Clean up "oops" commits before submitting;
* Follow the [coding style guide](https://github.com/opencv/opencv/wiki/Coding_Style_Guide).
