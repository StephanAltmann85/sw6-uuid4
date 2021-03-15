# SW6 UUID4

This project is based on https://github.com/gpakosz/uuid4. This fork simply removes the dashes between the chunks to provide sw6 compatible ids.

## Compiling for Windows

There is a Visual Studio 2015 solution in the `_win-vs14/` folder.

## Compiling for Linux or Mac

There is a GNU Make 3.81 `MakeFile` in the `_gnu-make/` folder:

    $ make -j -C _gnu-make/

## Compiling for Mac

See above if you want to compile from command line. Otherwise there is an Xcode
project located in the `_mac-xcode/` folder.

## Compiling for iOS

There is an Xcode project located in the `_ios-xcode/` folder.

If you prefer compiling from command line and deploying to a jailbroken device
through SSH, use:

    $ make -j -C _gnu-make/ platform=ios architecture=arm64 CC="$(xcrun --sdk iphoneos --find clang) -isysroot $(xcrun --sdk iphoneos --show-sdk-path) -arch arm64" postbuild="codesign -s 'iPhone Developer'"

## Compiling for Android

You will have to install the Android NDK, and point the `$NDK_ROOT` environment
variable to the NDK path: e.g. `export NDK_ROOT=/opt/android-ndk` (without a
trailing `/` character).

Next, the easy way is to make a standalone Android toolchain with the following
command:

    $ $NDK_ROOT/build/tools/make_standalone_toolchain.py --arch=arm64 --api 21 --install-dir=/tmp/android-toolchain

Now you can compile the example by running:

    $ make -j -C _gnu-make/ platform=android architecture=arm64 CC=/tmp/android-toolchain/bin/aarch64-linux-android-gcc CXX=/tmp/android-toolchain/bin/aarch64-linux-android-g++