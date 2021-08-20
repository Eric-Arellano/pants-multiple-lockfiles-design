# disjoint-platform-binaries_shared-lockfile

## Setup

The three binaries use `--platforms`, so they need "platform-aware" lockfiles, per 
https://github.com/pantsbuild/pants/issues/12612. 

Here, they all share the same lockfile, even 
though they use different platforms. The lockfile must work with all the used platforms.

## Resolve logic

### `./pants package` and `./pants run`

Every binary shares the same resolve.
