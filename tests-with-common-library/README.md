# tests-with-common-library

## Setup

Because the two tests have conflicting requirements for the same `Django` project, they each use 
their own resolve. 

However, they both depend on `:util`, which depends on the same `:colors` 
third-party dep. `:util` does not have a dedicated `resolve` because it's a `python_library` so 
cannot set one. Note that `:colors` has a floating requirement, and the lockfiles have slightly 
different versions for `ansicolors` because they were generated at different times.

## Resolve logic

### `./pants test`

Each test runs as a separate process and uses its own resolve.

### `./pants typecheck` and Pylint

Depends on your specs:

* only the `python_tests` -> partition into two runs.
* only the `python_library` -> use either of the lockfiles, as both are compatible with the 
  library. Only run once.
* a single `python_tests` and the `python_library` -> run together using the test's resolve, as 
  the `python_library` is compatible with it.
* all targets -> partition into two runs, and only directly run on the `python_library` in 
  one of them??
    * It would be bad UX (I think) to run on the same `python_library` twice, meaning that we would 
      error twice.
    * The `python_library` does need to be present in both runs, though.

### Note about `python_library` and floating deps

Reminder that the two lockfiles have different versions for `ansicolors`, which is possible 
because the `python_requirement_library` is floating.

This could be a problem that the 
`python_library` gets its dependency pinned from either of the lockfiles, e.g. if only one of them
actually works. But the thinking is that if that's the case, then the `python_requirement_library` 
needs to be tightened to reflect this so that both lockfiles use the correct version.

For example, it would probably lead to issues if the `python_requirement_library` was something as 
loose as `Django`, and one lockfile was Django 2 and another Django 3. In that case, the user 
should create two distinct targets for the same project, and the `python_library` choose which 
one it's intended to work with. Although, this is subtle.

Another wildcard is to let `python_library` targets set a preferred (required?) resolve, but that
gets into issues w/ how to handle transitive dependencies all needing to use the same resolve,
which breaks that `library` working with lots of code (maybe okay?).