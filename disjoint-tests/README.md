# disjoint-tests

## Setup

Because the two tests have conflicting requirements for the same `Django` project, they each use 
their own resolve.

## Resolve logic

### `./pants test`

Each test runs as a separate process and uses its own resolve.

### `./pants typecheck` and Pylint

Partition into two runs.
