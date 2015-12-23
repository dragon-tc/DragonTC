![alt text](http://imgur.com/gFcFcZ7.png)
What is DragonTC?
-----------------
DragonTC is a build system for compiling custom clang toolchains. These toolchains contain the latest AOSP patches and things not included in AOSP clang, such as the latest LTO from binutils and Polly compiled and automatically linked into tools.

Why use custom Clang?
---------------------
Google has been slowly moving away from GCC for a while now, so we believe that we should get ahead of the toolchain game and start now! Furthermore, AOSP modules that are compiled with clang can easily be optimized with the new LTO and Polly options.
