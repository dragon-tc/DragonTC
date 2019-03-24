![alt text](http://imgur.com/gFcFcZ7.png)

DragonTC is a build system for compiling custom clang toolchains. These toolchains contain the latest AOSP patches(where applicable) and things not included in AOSP clang, such as LTO and Gold plugins, Polly compiled and automatically linked into tools, improved krait optimizations (-mcpu=krait2), and annoying flags such as -Werror, -Wfatal-errors, and -Weverything internally disabled. DragonTC compilers are also built with -O3, -pthread, and -fopenmp in order to reduce compile time when used for ROMs.

### Why Use Custom Clang ?

Google has been slowly moving away from GCC for a while now, so we believe that we should get ahead of the toolchain game and start now! Furthermore, AOSP modules that are compiled with clang can easily be optimized with the new LTO and Polly options.

### How To Build DragonTC ?

- Setup Build Environment:
  - For Debian and Ubuntu:
    ```
    sudo apt-get install build-essential git git-svn bc binfmt-support libllvm-3.6-ocaml-dev llvm-3.6 llvm-3.6-dev llvm-3.6-runtime cmake automake autogen autoconf autotools-dev libtool shtool python m4 gcc libtool zlib1g-dev libomp-dev
    ```

- Run the following commands in terminal to set up work directory:
    ```
    mkdir dtc & cd dtc
    repo init -u https://github.com/dragon-tc/DragonTC -b master
    repo sync -j$(nproc --all) -c -f
    ```

- Run the following to build your desired toolchain:
    ```
    cd build
    ./version
    ```
    Where "version" is `5.0``6.0` or `7.0`.

- To optimize the toolchain for your local system, run with the 'opt' argument. Example:
    ```
    ./version opt
    ```
### How To Use DragonTC In AOSP? (outdated)

* Either clone a prebuilt or build your own toolchain and place it in prebuilts/clang/linux-x86/host/your_version (3.7.1 is the prefered version)
* Change the version in build/core/clang/config.mk to reflect the directory you placed it in. 
* Either clone ours, or cherry-pick our changes to [prebuilts/ndk](https://github.com/dragon-tc/android_prebuilts_ndk/commits/master) and [frameworks/rs](https://github.com/dragon-tc/android_frameworks_rs/commits/master).
* **[WIP]** Cherry-pick our DragonTC support commit in [build](https://github.com/dragon-tc/android_build/commit/c020e9a1abb543fc687ccd49bb1d1ab95acc75cf).