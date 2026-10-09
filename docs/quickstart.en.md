# First login

## You will need

- A Blackhole account activated by the CI-SSLab team.
- The login node hostname provided by the cluster administrator (shown here as `LOGIN_HOST`).
- An SSH client. On Windows, use OpenSSH in PowerShell; on macOS and Linux, use a terminal.
- A project SLURM account if required (shown here as `PROJECT_ACCOUNT`).

## Connect

```sh
ssh USERNAME@LOGIN_HOST
```

For an initial check, list the available partitions and consult the job examples:

```sh
sinfo
```

Submit compute workloads with `sbatch` or `srun`; do not run heavy workloads on the login node. If the cluster requires an account, add `--account=PROJECT_ACCOUNT` to SLURM commands.

## Next steps

- [Configure an SSH key](access/ssh.md)
- [Connect with VS Code](environment/vscode.md)
- [Submit your first job](slurm/jobs.md)

!!! warning "Keep secrets out"
    Do not put passwords, private keys, tokens, or confidential data in the site files, repositories, or shared scripts.
