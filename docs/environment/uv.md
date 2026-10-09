# Python con uv

[`uv`](https://docs.astral.sh/uv/) gestisce interpreti, ambienti virtuali e dipendenze Python. Esegui questi comandi sul cluster, nella directory del progetto.

## Installa uv nel tuo account

Usa il metodo di installazione approvato dal team e dal cluster. Se è disponibile `curl` e le policy locali lo consentono:

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Poi riapri la shell o aggiorna `PATH` secondo le istruzioni mostrate dall'installer. In ambienti gestiti, preferisci il modulo o il pacchetto fornito dagli amministratori.

## Crea un progetto

```sh
cd ~/progetto
uv init --bare
uv python pin 3.12
uv add numpy pandas
uv run python -c "import numpy; print(numpy.__version__)"
```

`uv.lock` registra le versioni risolte: includilo nel repository per rendere ripetibile l'installazione. Mantieni l'ambiente `.venv` locale al progetto e aggiungilo a `.gitignore`.

## Nei job SLURM

```sh
uv sync --locked
uv run python train.py
```

Il job deve avere accesso ai pacchetti già scaricati o alla rete secondo le policy del cluster. Se i nodi di calcolo non hanno accesso a Internet, sincronizza prima l'ambiente su un nodo consentito o segui la procedura del team.
