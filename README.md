# Git hooks for Quantas

## Under Development

The idea is that results will be referenced by `refs/results/deadbeef...` where
`deadbeef...` is the hash of the commit that was used to generate the results.

Currently, this hook creates these convenient git refs on the server, but not
the client.

## post-receive
This hook is to be installed in the git repository that you push your code to to
be run. It is placed in `.git/hooks/post-receive`. It must be executable
(use `chmod +x`).

`post-receive` will run `make run` on any code pushed on the `run` branch, and
commit the results and tag them with `results`. This commit is not added to the
`run` branch, but can be fetched with `git fetch --tags`.
