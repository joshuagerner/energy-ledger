# energy-ledger

Static site served by nginx, deployed by `git pull`.

## Deployment

`docker-compose.yml` mounts `./html` read-only into the nginx container.
nginx serves files directly from disk, so a `git pull` on this repo is
the entire deploy — no container restart, no rebuild. The container
only needs to be (re)started if `docker-compose.yml` itself changes.

## Content ownership

`html/ledger.html` is generated in a separate Claude session/project
called **HAPowerManagement_Costing**. Do not hand-edit its content here
— changes should come from that project and be pasted/committed in from
there. `html/index.html` just redirects to `ledger.html` and is fine to
edit in this repo.
