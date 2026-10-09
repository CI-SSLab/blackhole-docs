# Job examples

Save scripts in your project filesystem and submit them from the login node with `sbatch`. The run times below show the stated maximums; lower them when your workload finishes sooner.

## Standard CPU job · 24 hours

`cpu.sbatch`:

```bash
#!/usr/bin/env bash
#SBATCH --job-name=cpu-analysis
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

If `logs/` does not exist before `sbatch`, create it first: SLURM opens output files before starting the script.

## Research GPU job · up to 7 days

`gpu.sbatch` (partition `xgpu1`, RTX 4060):

```bash
#!/usr/bin/env bash
#SBATCH --job-name=gpu-training
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

For the Titan X, replace `xgpu1` with `xgpu2`. CPU and RAM values are examples to confirm with the team; the research time limit may require a specific account or QoS not listed here.

## Submit and monitor

```sh
sbatch cpu.sbatch
squeue --me
scancel JOB_ID
```

Use `scancel` only for your own job. For short interactive jobs, ask the team for the `srun` procedure and its limits.
