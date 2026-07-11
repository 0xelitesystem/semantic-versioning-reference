# Zero dot x caveats

While the major version is `0` (any `0.y.z` release), anything may change at any time and the public API is not considered stable. This is the initial-development phase, and SemVer explicitly withholds its usual compatibility promise here.

## What 0.x actually means

During `0.x`, breaking changes can land in a minor bump. `0.2.0` and `0.3.0` may be wildly incompatible, and that is allowed by the spec. You are telling users the shape of the software is still moving. Do not read `0.5.0` to `0.6.0` as a safe upgrade the way you would read `1.5.0` to `1.6.0`.

## How ranges shift under 0.x

Range operators key off the leftmost nonzero digit, so under `0.x` the caret protects a different position than usual.

- `^0.2.3` allows `>=0.2.3 <0.3.0`. The leftmost nonzero digit is the minor (`2`), so the caret pins the minor and lets only the patch float. This behaves like a tilde would on a `1.x` version.
- `^0.0.3` allows `>=0.0.3 <0.0.4`. Now the leftmost nonzero digit is the patch (`3`), so the caret pins everything and accepts only that exact version.

This is why `^0.2.3` feels stricter than people expect: at `0.x` the caret assumes the minor might break you.

## The move to 1.0.0

Version `1.0.0` defines the public API. Once you release it, the MAJOR, MINOR, PATCH rules apply in full and breaking changes require a major bump. Cut `1.0.0` as soon as your software is used in production or has a stable interface others depend on. Stay on `0.x` only while the design is genuinely unstable.

## The practical risk

Depending on a `0.x` library means every minor update is a potential break, so pin those dependencies tightly (an exact version or a tilde-style range) and read the changelog before every upgrade. Treat a long-lived `0.x` project as a signal to review its stability before you build something important on top of it.
