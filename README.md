# git-cache
A simple script to cache git repositories and packages locally. If git-cache
has not been initialized, it will fall back to do checkouts from the remote
repository. Otherwise it will transparently cache repositories in it's cache
folder, ideally not touching the network if a requested commit / tag can be
cloned from the cache.

## Use Case
This is particularly useful when many copies of a git repository are needed,
such as when running a CI that requires a clean directory to build with.

## Example Setup

Either add the `git-cache` binary to the `PATH` or directly execute it.

Initialize the git repository (by default it creates a `${HOME}/.gitcache`).
```
git-cache init
```

Use git-cache to clone the repository as needed.
```
git-cache clone https://github.com/MaxMusterman/ExampleRepo HEAD test1
git-cache clone https://github.com/MaxMusterman/ExampleRepo HEAD test2
```

_The first clone may take a while since it needs to fetch the repo and add it
to the cache. The second clone should be able to fetch the repo from the
cache._