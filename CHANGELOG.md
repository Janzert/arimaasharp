# Changelog

Changes in this fork of
[lightvector/arimaasharp](https://github.com/lightvector/arimaasharp).
Releases are tagged with their date (`v2026.10.6`). The fork starts from
upstream's 2021 public release of the source (commit `5f336a7`).

## Unreleased

- **Fixed:** a `stop` sent right after `go`, before the search thread has
  started or found its root moves, is answered with a move from a quick
  one-turn search. Upstream logged "Bot tried to make illegal move:" and
  sent no `bestmove`, so a controller waiting for one lost on time.
  Searches that find a move are unchanged.
- The engine manifest (`engine.json`) is kept in the repository. The
  release workflow adds each release's version and downloads. It now
  lists the `depth` option.

## 2026.10.6 (2026-10-06)

The first release of the fork. Each release publishes builds for Linux,
Windows and macOS with an engine manifest (`engine.json`, AEI's
`ENGINE_MANIFEST.md`) that controllers can install from.

- **Added:** a CMake build for GCC, Clang, or clang-cl on Windows, using
  `std::thread` so Boost isn't needed. `-DSHARP_DEV=ON` builds the
  developer command line instead of editing `isDev` in `main.cpp`.
- **Changed:** the `verbose` AEI option works outside dev builds. It logs
  each finished iteration and new best move with its principal
  variation, which an analysis client can show while Sharp thinks.
- **Fixed:** compiles with current compilers and standard libraries:
  missing `<cmath>` and `<cstdlib>` includes, `book.cpp`'s own
  `abs(double)` that clashed with the standard one (same values),
  `std::ostream` built with a null buffer, and an unused Boost include.
  `runBasicTests` passes, including its fixed search results.
- **Fixed:** builds on macOS, using the Unix timer.
- CI builds and runs the self-tests on Linux, macOS and Windows.
