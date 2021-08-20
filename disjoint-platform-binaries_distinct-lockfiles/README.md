# two-disjoint-platform-binaries_distinct-lockfiles

## Setup

The two binaries use `--platforms`, so they need "platform-aware" lockfiles, per 
https://github.com/pantsbuild/pants/issues/12612.

Here, they both use their own lockfile, but it would have been valid to share.

## Resolve logic

### `./pants package` and `./pants run`

Each binary is packaged as a separate process and uses its own resolve.
