---
homepage: true
---

# Computing for research

Blackhole is the HPC infrastructure of the **Computational Intelligence and Smart Systems Lab (CI-SSLab)**. This documentation explains how to access resources and use them reproducibly.

<div class="grid cards" markdown>

-   :material-console-network: **Remote access**

    ---
    Connect over SSH and work from your editor without moving your project off the cluster.

    [:octicons-arrow-right-24: SSH guide](access/ssh.md)

-   :material-cpu-64-bit: **Compute resources**

    ---
    Choose a CPU or GPU partition and submit work through SLURM.

    [:octicons-arrow-right-24: Partitions and jobs](slurm/partitions.md)

-   :material-language-python: **Reproducible environment**

    ---
    Set up VS Code and manage Python environments and dependencies with uv.

    [:octicons-arrow-right-24: Python setup](environment/uv.md)

</div>

!!! info "Before connecting"
    Ask your project lead for the SSH host, your account, and any SLURM account name. This guide contains no credentials or private data.

## Start here

1. [Prepare your first login](quickstart.md)
2. [Configure SSH](access/ssh.md)
3. [Open a remote VS Code session](environment/vscode.md)
4. [Submit a CPU or GPU job](slurm/jobs.md)

> The commands and limits here describe Blackhole's initial configuration. If your cluster administrator gives you different instructions, follow the configuration they provide.
