# Git hooks for Quantas

## `post-receive`

This hook is to be installed in the git repository that you push your code to to
be run. It is placed in `.git/hooks/post-receive`. It must be executable
(use `chmod +x`).

`post-receive` will run `make run` on any code pushed on the `run` branch, and
commit the results. This commit is not added to the `run` branch but is
referenced by `refs/results/deadbeef...` where `deadbeef...` is the hash of the
commit that was used to generate the results.

### Fetching results

You can fetch results with

``` sh
git fetch <remote> refs/results/deadbeef...:refs/results/deadbeef...
```

E.g. to fetch the result for HEAD, use:

``` sh
git fetch <remote> refs/results/$(git rev-parse @):refs/results/$(git rev-parse @)
```

Or fetch all results with:

``` sh
git fetch <remote> refs/results/*:refs/results/*
```
