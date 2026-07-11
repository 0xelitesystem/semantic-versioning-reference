# Version ranges

A version range is a rule that says which versions of a dependency you accept, written in a dependency file like `package.json`. The two you see most are the caret `^` and the tilde `~`, and they differ in how much they let a version drift upward.

## Caret: allow non-breaking updates

The caret allows changes that do not modify the leftmost nonzero digit. For a normal `1.x` version this means you get new minors and patches but not new majors.

`^1.2.3` allows `>=1.2.3 <2.0.0`.

So `^1.2.3` would accept `1.2.9`, `1.5.0`, and `1.99.4`, but not `2.0.0`. This is the common default because it tracks all backward-compatible releases automatically.

## Tilde: allow patch updates only (when minor is given)

The tilde allows patch-level changes when a minor version is specified. It pins the minor and lets only the patch float.

`~1.2.3` allows `>=1.2.3 <1.3.0`.

So `~1.2.3` accepts `1.2.4` and `1.2.20`, but not `1.3.0`. Use the tilde when you want bug fixes but no new features.

## Comparison operators

You can state bounds directly with `>=`, `>`, `<=`, `<`, and combine them:

- `>=1.2.0` accepts that version and anything higher.
- `>=1.2.0 <1.5.0` accepts a half-open window.
- `<=2.3.1` accepts that version and anything lower.

## Exact pins

An exact version with no operator, like `1.4.7`, pins to only that release. Use this when you need fully reproducible installs and accept manual upgrades.

## Wildcards

The `x` (or `*`) wildcard fills in whatever the position allows:

- `1.2.x` matches any patch in the `1.2` line, equal to `>=1.2.0 <1.3.0`.
- `1.x` matches any minor and patch in the `1` line, equal to `>=1.0.0 <2.0.0`.
- `*` matches any version at all.

In practice `1.2.x` behaves like `~1.2.0` and `1.x` behaves like `^1.0.0`.
