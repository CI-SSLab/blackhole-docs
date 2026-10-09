# SLURM partitions

SLURM allocates requested resources when a job starts. Choose a partition for your workload and ask the team which account to attach if required.

| Partition | Listed resource | Typical use |
|---|---|---|
| `xcpu` | CPU | preprocessing, simulations, and CPU compute |
| `xgpu1` | NVIDIA RTX 4060 GPU | GPU experiments that fit available memory |
| `xgpu2` | NVIDIA Titan X GPU | GPU experiments that fit available memory |

Request one GPU with `--gres=gpu:1`. Confirm RAM, CUDA versions, CPUs per device, and any machine-specific options with the team; this first guide does not assume values that have not been provided.

## Time limits

- **Standard:** up to `24:00:00` per job.
- **Research:** up to `7-00:00:00` per job, if authorized for the project.

These are run-time limits, not partition names. If the cluster uses separate QoS or accounts to enforce them, ask the administrator for the actual values before submitting a job.

## Check the queue

```sh
sinfo
squeue --me
```

To reduce queue time, request only the CPU, memory, GPU, and run time you need. SLURM may terminate a job that exceeds its limit.
