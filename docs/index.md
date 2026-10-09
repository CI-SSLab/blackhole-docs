---
homepage: true
---

# Calcolo per la ricerca

Blackhole è l'infrastruttura HPC del **Computational Intelligence and Smart Systems Lab (CI-SSLab)**. Questa documentazione raccoglie le procedure per accedere alle risorse e usarle in modo riproducibile.

<div class="grid cards" markdown>

-   **Accesso remoto**

    ---
    Collegati via SSH e lavora dal tuo editor senza trasferire il progetto fuori dal cluster.

    [Guida SSH](access/ssh.md)

-   **Risorse di calcolo**

    ---
    Scegli la partizione CPU o GPU e invia il lavoro tramite SLURM.

    [Partizioni e job](slurm/partitions.md)

-   **Ambiente riproducibile**

    ---
    Configura VS Code e gestisci ambienti e dipendenze Python con uv.

    [Setup Python](environment/uv.md)

-   **Container e Docker**

    ---
    Riusa immagini Docker nei job SLURM con il runtime container approvato dal cluster.

    [Guida container](environment/containers.md)

</div>

!!! info "Prima di collegarti"
    Chiedi al responsabile del progetto l'host SSH, il tuo account e l'eventuale nome dell'account SLURM. Questa guida non contiene credenziali o dati riservati.

## Parti da qui

1. [Prepara il primo accesso](quickstart.md)
2. [Configura SSH](access/ssh.md)
3. [Apri una sessione remota con VS Code](environment/vscode.md)
4. [Invia un job CPU o GPU](slurm/jobs.md)

> I comandi e i limiti riportati descrivono la configurazione iniziale di Blackhole. Se le indicazioni ricevute dal team differiscono, fai riferimento alla configurazione comunicata dal responsabile del cluster.
