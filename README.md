## OpenCV: Open Source Computer Vision Library
---
### Cross compilation for riscv64 with musl libc
#### Install cross compilation tools:
```
wget https://musl.cc/riscv64-linux-musl-cross.tgz
tar xvf riscv64-linux-musl-cross.tgz
export PATH=/path/to/riscv64-linux-musl-cross/bin:$PATH
```
#### Getting OpenCV Source Code
```
git clone https://github.com/elliott10/opencv.git
```
#### Building OpenCV
```
mkdir -p opencv/build && cd opencv/build
cmake -DCMAKE_TOOLCHAIN_FILE=../platforms/linux/riscv64-musl-gcc.toolchain.cmake -DCMAKE_INSTALL_PREFIX=$PWD/install  ../
make -j8
make install
```
The binaries will be placed in this directory: `opencv/build/bin/`

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
