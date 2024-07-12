# Devrel documentation

The docs will go live on the [Polygon Knowledge Layer](...).

## Run docs locally

### Prerequisites

1. [Python 3.12](https://www.python.org/downloads/).
2. Install [`virtualenv`](https://pypi.org/project/virtualenv/):

```sh
pip3 install virtualenv
```

### Setup

1. Clone the repository.
2. `cd` to the root.
3. Run the `scripts/serve_docs.sh` script. You may need to make the script executable: `chmod +x scripts/serve_docs.sh`

```sh
sh scripts/serve_docs.sh
```

The site comes up at http://127.0.0.1:8000/.

If it runs and renders well here, it will render correctly on the Knowledge Layer. If there are any unfixed errors breaking the local build, it will probably break on import to the Knowledge Layer.

## Style guide

We are using the [Microsoft Style Guide](https://learn.microsoft.com/en-us/style-guide/welcome/).

## Contact and raising issues

- For technical and documentation problems, raise an issue on the [devrel-docs repo](https://github.com/0xPolygon/devrel-docs/issues).
- Join our [Discord](https://discord.gg/0xpolygondevs).
