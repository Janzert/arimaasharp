# bot_sharp (Janzert's fork)

This is a fork of [lightvector/arimaasharp](https://github.com/lightvector/arimaasharp),
kept so that Sharp builds with current compilers and can serve as an
analysis engine for desktop clients. It is not maintained or endorsed by
Sharp's author. The original README follows the build notes.

## Building

Sharp needs a C++11 compiler and CMake 3.16 or later; Boost isn't needed.

    cmake -S . -B build
    cmake --build build

On Windows, build from a Visual Studio developer prompt with clang-cl
(MSVC's own compiler doesn't accept the GCC builtins Sharp uses):

    cmake -S . -B build -G Ninja -DCMAKE_CXX_COMPILER=clang-cl
    cmake --build build

Run the engine as `build/sharp aei`. Besides the usual AEI options,
`setoption name verbose value true` logs each search iteration and new
best move. A `stop` sent right after `go`, before the search has found a
move, is answered with a move from a quick one-turn search; upstream sent
no `bestmove` then.

`-DSHARP_DEV=ON` builds the developer command line instead, which takes a
command first. `build/sharp runBasicTests` runs the self-tests.

## Original README

This repo is a public archive of the source code for bot_sharp, a project that was started all the way back in 2007, and which by 2015 became the strongest available bot for the game Arimaa: [http://arimaa.com/arimaa/](http://arimaa.com/arimaa/). Since then, Sharp has been superseded by much stronger and more advanced bots written by others based on deep learning and/or AlphaZero-style methods.

Compiled binaries can be found here: http://arimaa.com/arimaa/forum/cgi/YaBB.cgi?board=devTalk;action=display;num=1526353703

The release of this code is mostly to make it available out of historical interest. No further development is planned, and no support is being provided to users wishing to run the above binaries or wishing to compile and run it from source.

See LICENSE file for license.




