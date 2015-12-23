![alt text](http://imgur.com/gFcFcZ7.png)
What is DragonTC?
-----------------
DragonTC is a build system for compiling custom clang toolchains. These toolchains contain the latest AOSP patches and things not included in AOSP clang, such as the latest LTO from binutils and Polly compiled and automatically linked into tools.

Why use custom Clang?
---------------------
Google has been slowly moving away from GCC for a while now, so we believe that we should get ahead of the toolchain game and start now! Furthermore, AOSP modules that are compiled with clang can easily be optimized with the new LTO and Polly options.

How do I build DragonTC?
------------------------
It's simple! Run the following commands in bash to get set up:
```
$ mkdir dtc
$ cd dtc
$ repo init -u https://github.com/dragon-tc/DragonTC -b master
$ repo sync -j(# of cores) -c -f
```

And run the following to build your desired toolchain:
```
$ cd build
$ . version
```
Where "version" is 3.5, 3.6, or 3.7.
