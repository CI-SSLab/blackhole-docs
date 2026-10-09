# Blackhole Docs

Bilingual documentation for the Blackhole HPC infrastructure at CI-SSLab, built with MkDocs Material.

## Local preview

```sh
uv run --with mkdocs-material --with mkdocs-static-i18n mkdocs serve
```

Or install the pinned project requirements first:

```sh
pip install -r requirements.txt
mkdocs serve
```

## Build

```sh
mkdocs build --strict
```

GitHub Actions builds every pull request. A separate workflow deploys GitHub Pages from `main` only. Deployment does not run for feature-branch pushes.

## Configuration notes

Hostnames, account names, and cluster-specific QoS values are intentionally placeholders until confirmed by the cluster administrators. Do not commit credentials, private keys, tokens, or confidential data.

See [ASSETS.md](ASSETS.md) for the source and handling of the official university logo assets.
