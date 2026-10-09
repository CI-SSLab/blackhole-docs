# VS Code on the cluster

The **Remote - SSH** extension opens a local window connected over SSH. Your code and tools stay on the cluster; the interface runs on your computer.

1. Install Visual Studio Code and Microsoft's *Remote - SSH* extension.
2. Add the `blackhole` host to `~/.ssh/config` as described in the [SSH guide](../access/ssh.md).
3. Open the command palette and select **Remote-SSH: Connect to Host...** → `blackhole`.
4. Open your project folder in the remote session.
5. Select the Python interpreter in the environment created with [uv](uv.md).

Use Remote - SSH for editing, inspection, and light tasks. Submit training and compute workloads as SLURM jobs; an editor session does not reserve compute resources.

If VS Code cannot find your key, first check `ssh blackhole` in a terminal. Never paste private keys into VS Code or a chat.
