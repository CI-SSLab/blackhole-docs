# Primo accesso

## Ti serve

- Un account Blackhole attivato dal team CI-SSLab.
- L'hostname del nodo di accesso, comunicato dal responsabile del cluster (qui: `LOGIN_HOST`).
- Un client SSH. Su Windows puoi usare OpenSSH in PowerShell; su macOS e Linux il terminale.
- Un account SLURM di progetto, se richiesto (qui: `PROJECT_ACCOUNT`).

## Collegati

```sh
ssh USERNAME@LOGIN_HOST
```

Per un primo controllo, consulta le partizioni disponibili e la documentazione dei job:

```sh
sinfo
```

Invia i calcoli con `sbatch` o `srun`; non eseguire lavori pesanti sul nodo di login. Se la configurazione del cluster richiede un account, aggiungi `--account=PROJECT_ACCOUNT` ai comandi SLURM.

## Passi successivi

- [Configura una chiave SSH](access/ssh.md)
- [Collegati con VS Code](environment/vscode.md)
- [Invia il primo job](slurm/jobs.md)

!!! warning "Non condividere segreti"
    Non inserire password, chiavi private, token o dati riservati nei file del sito, nei repository o negli script condivisi.
