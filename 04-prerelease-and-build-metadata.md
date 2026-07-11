# Pre-release and build metadata

SemVer lets you tack two optional labels onto a version: a pre-release tag after a hyphen and build metadata after a plus sign. A full example using both is `1.0.0-beta+exp.sha.5114f85`.

## Pre-release identifiers

A pre-release version appends a hyphen and a series of dot-separated identifiers, marking a release as not yet ready for general use. Common patterns:

- `1.0.0-alpha`
- `1.0.0-alpha.1`
- `1.0.0-beta.2`
- `1.0.0-rc.1`

Identifiers may contain letters, numbers, and hyphens. Numeric identifiers must not have leading zeros.

## Pre-release precedence

A pre-release version has lower precedence than the associated normal version. This is the rule people forget most often.

`1.0.0-alpha` is less than `1.0.0`.

So `1.0.0-alpha`, `1.0.0-beta`, and `1.0.0-rc.1` all come before the finished `1.0.0`. That is why a range like `^1.0.0` will not automatically pull in `2.0.0-alpha`; pre-releases are treated as earlier, not as a shortcut to the next line.

## How pre-release identifiers are compared

When two versions share the same major, minor, and patch, you compare their pre-release parts identifier by identifier, left to right:

- Numeric identifiers compare as numbers; `alpha.2` is less than `alpha.11`.
- Identifiers with letters compare as text in ASCII order.
- A numeric identifier always ranks lower than a non-numeric one.
- If all shared identifiers are equal, the version with more identifiers is greater, so `1.0.0-alpha` is less than `1.0.0-alpha.1`.

A worked chain: `1.0.0-alpha` < `1.0.0-alpha.1` < `1.0.0-beta.2` < `1.0.0-rc.1` < `1.0.0`.

## Build metadata

Build metadata appends a plus sign and dot-separated identifiers, such as `1.0.0+20130313144700` or `1.0.0-beta+exp.sha.5114f85`. Build metadata is ignored when determining precedence. Two versions that differ only in build metadata are considered the same version for ordering, so `1.0.0+build.1` and `1.0.0+build.2` rank equally. Use it to record a commit hash or build timestamp, not to signal a newer release.
