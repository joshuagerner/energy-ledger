# energy-ledger

Static site served by nginx, deployed by `git pull`.

## Deployment

The `energy-ledger` service is defined as a block in the main stack at
`/home/docker/docker-compose.yaml` (root-owned; not part of this repo),
on the `npm_proxy` network, port 8090, mounting this repo's `./html`
directory read-only by absolute path (`/home/josh/energy-ledger/html`).
nginx serves files directly from disk, so a `git pull` on this repo is
the entire deploy — no container restart, no rebuild. The container
only needs touching if the service block itself changes (image version,
port, mount path).

## Content ownership

`html/ledger.html` is generated in a separate Claude session/project
called **HAPowerManagement_Costing**. Do not hand-edit its content here
— changes should come from that project and be pasted/committed in from
there. `html/index.html` just redirects to `ledger.html` and is fine to
edit in this repo.
