# Semantic Versioning

Semantic Versioning (SemVer) is a naming convention for software releases that turns a version number into a promise about compatibility. It gives every release a three-part number so that anyone depending on your code can predict, at a glance, whether an upgrade is safe. This repo is a plain-language reference to the SemVer 2.0.0 specification, written for people who just want the rules and the exact syntax.

## The core idea

A SemVer number is written `MAJOR.MINOR.PATCH` (for example `2.4.1`), and each part signals a specific kind of change. You increment MAJOR for changes that break existing users, MINOR for backward-compatible features you add, and PATCH for backward-compatible bug fixes. The point is that the number itself communicates intent, so a consumer can set a dependency rule once and trust it. SemVer only works when maintainers actually honor these meanings, so the whole system is a shared agreement, not an automatic guarantee.

## What is inside

- `01-what-semver-means.md` the MAJOR.MINOR.PATCH format and how the numbers reset when you bump.
- `02-when-to-bump-which.md` concrete rules for choosing PATCH, MINOR, or MAJOR.
- `03-version-ranges.md` the caret, tilde, wildcard, and comparison syntax you look up in a dependency file.
- `04-prerelease-and-build-metadata.md` alpha and beta tags, build metadata, and how precedence is decided.
- `05-zero-dot-x-caveats.md` why 0.x is special and what the rules change to before 1.0.0.

## The stance

The rules here match the SemVer 2.0.0 spec, stated plainly with real version strings you can copy. Where the spec is strict, this reference is strict; where common tooling adds behavior on top, it says so.

## License

MIT. Copyright 0xelitesystem 2026.
