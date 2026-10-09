# Containers and Docker images

## Before you start

Blackhole is a shared cluster. Do not install or start a Docker daemon without instructions from the administrators. First check which runtime is available and allowed for SLURM jobs:

```bash
apptainer --version
```

If the command is unavailable, ask the cluster team which runtime to use. This guide shows how to reuse Docker/OCI images with [Apptainer](https://apptainer.org/docs/user/latest/docker_and_oci.html) when the cluster supports it; it does not assume Docker Engine is installed.

## Convert a Docker image to SIF

When cluster policy permits downloads from the registry, convert the image to a SIF file. Choose an approved storage location with enough space; for large images, follow local guidance on which node and filesystem to use.

```bash
apptainer pull python-3.12.sif docker://python:3.12-slim
```

Inspect the image and run a command inside it:

```bash
apptainer inspect python-3.12.sif
apptainer exec python-3.12.sif python --version
```

Apptainer recommends downloading the image once and then running the SIF file, instead of downloading the Docker image again at each launch.

## Use a container in a SLURM job

Place the `apptainer exec` command in the execution section of your SLURM script, after requesting the appropriate resources and partition according to the [job guide](../slurm/jobs.md):

```bash
apptainer exec "$SLURM_SUBMIT_DIR/python-3.12.sif" python train.py
```

The image and data must be in paths readable by the job. Check cluster rules for transfers, scratch storage, and persistent results.

## GPU jobs

For an image with CUDA libraries compatible with the node drivers, Apptainer can expose the host's NVIDIA devices and libraries with `--nv`:

```bash
apptainer exec --nv /path/to/cuda-image.sif nvidia-smi
```

Also request a GPU resource on the partition specified by the [SLURM instructions](../slurm/partitions.md). Check CUDA, driver, and image compatibility with the administrators; `--nv` alone does not install CUDA or allocate a GPU.

## If you specifically need Docker Engine

Docker Engine and access to its daemon require an administrator-managed setup. Ask whether the service is provided and which approved procedure to follow. Do not add your account to privileged groups or start Docker services on shared nodes yourself.
