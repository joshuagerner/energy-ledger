# energy-ledger

A static, single-page **Home Energy Ledger**: bill trend, the gap between billed and monitored usage, monitored devices by area, and gaps & recommendations.

## Layout

```
html/
  index.html   # redirects to ledger.html
  ledger.html  # the ledger page (self-contained HTML/CSS/JS)
```

There is no build step. The only external dependency is Google Fonts, loaded from the page itself.

## Viewing locally

Open `html/ledger.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8090 --directory html
```

## Deployment

The site is served by nginx, which mounts `./html` read-only and serves files directly from disk. Deploying is a `git pull` on the server, with no restart or rebuild.

## Updating the ledger

`html/ledger.html` is generated in a separate Claude project, **HAPowerManagement_Costing**, and is committed here as a dated snapshot. Don't hand-edit it in this repo: regenerate it there, then commit the new file here. `html/index.html` is only a redirect and is fine to edit directly.
