# Esempi di job

Salva gli script sul filesystem del progetto e inviali dal nodo di login con `sbatch`. I tempi qui sotto riflettono i massimi indicati: riducili quando il workload termina prima.

## Job CPU standard · 24 ore

`cpu.sbatch`:

```bash
#!/usr/bin/env bash
#SBATCH --job-name=analisi-cpu
#SBATCH --partition=xcpu
#SBATCH --time=24:00:00
#SBATCH --cpus-per-task=4
#SBATCH --mem=16G
#SBATCH --output=logs/%x-%j.out
#SBATCH --error=logs/%x-%j.err

set -euo pipefail
mkdir -p logs
uv sync --locked
uv run python analysis.py
```

Se `logs/` non esiste prima di `sbatch`, crea la cartella in anticipo: SLURM apre i file di output prima di avviare lo script.

## Job GPU research · fino a 7 giorni

`gpu.sbatch` (partizione `xgpu1`, RTX 4060):

```bash
#!/usr/bin/env bash
#SBATCH --job-name=training-gpu
#SBATCH --partition=xgpu1
#SBATCH --gres=gpu:1
#SBATCH --time=7-00:00:00
#SBATCH --cpus-per-task=4
#SBATCH --mem=24G
#SBATCH --output=logs/%x-%j.out
#SBATCH --error=logs/%x-%j.err

set -euo pipefail
mkdir -p logs
uv sync --locked
uv run python train.py
```

Per la Titan X sostituisci `xgpu1` con `xgpu2`. I valori CPU e RAM sono esempi da verificare con il team; il limite research può richiedere un account o una QoS specifici, non noti in questa guida.

## Invia e monitora

```sh
sbatch cpu.sbatch
squeue --me
scancel JOB_ID
```

Usa `scancel` solo sul tuo job. Per job interattivi brevi, chiedi al team la procedura `srun` e i limiti previsti.
