# Python with uv

[`uv`](https://docs.astral.sh/uv/) manages Python interpreters, virtual environments, and dependencies. Run these commands on the cluster, inside your project directory.

## Install uv in your account

Use an installation method approved by the team and the cluster. If `curl` is available and local policy allows it:

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Then reopen your shell or update `PATH` as shown by the installer. On managed systems, prefer the module or package provided by administrators.

## Create a project

```sh
cd ~/project
uv init --bare
uv python pin 3.12
uv add numpy pandas
uv run python -c "import numpy; print(numpy.__version__)"
```

`uv.lock` records the resolved versions: commit it to make installations reproducible. Keep `.venv` local to the project and add it to `.gitignore`.

## In SLURM jobs

```sh
uv sync --locked
uv run python train.py
```

The job must be able to access already-downloaded packages or the network, according to cluster policy. If compute nodes have no Internet access, sync the environment on an allowed node first or follow the team's process.
