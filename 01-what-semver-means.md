# What SemVer means

A SemVer version is three numbers separated by dots, written `MAJOR.MINOR.PATCH`, such as `2.4.1`. Each position has a fixed meaning, and each is a non-negative integer that never contains leading zeros.

## The three numbers

- MAJOR (the `2` in `2.4.1`) changes when you make an incompatible change that can break existing users.
- MINOR (the `4`) changes when you add functionality in a backward-compatible way.
- PATCH (the `1`) changes when you make backward-compatible bug fixes.

The numbers convey compatibility intent. A person reading `2.4.1` should be able to infer, without reading your code, roughly how risky moving to a newer version is. That is the entire value of the scheme.

## How increments reset lower numbers

When you bump a number, every number to its right resets to zero. This keeps the version space clean and predictable.

- Bumping PATCH just increases the patch: `1.4.7` becomes `1.4.8`.
- Bumping MINOR increases the minor and resets patch to `0`: `1.4.7` becomes `1.5.0`.
- Bumping MAJOR increases the major and resets both minor and patch to `0`: `1.5.0` becomes `2.0.0`.

So a realistic release history reads like this: `1.4.7` (a bug fix), then `1.5.0` (a new feature added cleanly), then `2.0.0` (a breaking change). You never write `1.5.3` and then jump the minor to `1.6.3`; the patch always drops back to `0` when the minor moves.

## Why the ordering matters

Versions compare left to right, number by number. `2.0.0` is greater than `1.5.0`, which is greater than `1.4.7`. This ordering is what lets tools decide which release is newer and which range a candidate version falls into. Because the reset rule is strict, there is exactly one correct next version for any given kind of change.
