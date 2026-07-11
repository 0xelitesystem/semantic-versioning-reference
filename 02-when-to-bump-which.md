# When to bump which number

Pick the number to increment by asking one question: does this change break existing users? If yes, bump MAJOR. If it only adds something without breaking anyone, bump MINOR. If it fixes a bug without changing behavior anyone relied on, bump PATCH.

## PATCH: backward-compatible bug fixes

Increment PATCH when you correct behavior that was already supposed to work, and nothing about the public interface changes. Examples: fixing an off-by-one error, correcting a wrong return value, patching a memory leak, or updating a typo in an error message. Callers who upgrade should see only the bug disappear.

Example: `1.4.7` becomes `1.4.8`.

## MINOR: backward-compatible new features

Increment MINOR when you add functionality that existing callers can ignore. Anything additive belongs here. Examples: adding a new function, adding a new optional parameter with a default, adding a new field to a response, or marking something as deprecated (but not yet removing it). Old code keeps working; new code gets the new capability.

Example: `1.4.7` becomes `1.5.0`.

Adding an optional parameter is a MINOR change precisely because callers who do not pass it behave exactly as before.

## MAJOR: backward-incompatible changes

Increment MAJOR when a change can break code that depends on you. Examples: removing a function, renaming a public method, changing a function signature so old calls fail, changing a default value, tightening validation so previously accepted input is rejected, or changing the type of a returned value.

Example: `1.5.0` becomes `2.0.0`.

Removing a function or changing its signature is always MAJOR, even if you think few people use it. The version number is a promise, and breaking that promise silently is the one thing SemVer exists to prevent.

## The quick test

If a caller upgrades and their code still compiles and behaves the same, it was MINOR or PATCH. If it might not, it was MAJOR.
