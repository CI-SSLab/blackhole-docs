# Container e immagini Docker

## Prima di iniziare

Blackhole è un cluster condiviso: non installare o avviare un demone Docker senza indicazioni degli amministratori. Verifica prima quale runtime è disponibile e consentito per i job SLURM:

```bash
apptainer --version
```

Se il comando non è disponibile, chiedi al team del cluster quale runtime usare. Queste istruzioni mostrano come riutilizzare immagini Docker/OCI con [Apptainer](https://apptainer.org/docs/user/latest/docker_and_oci.html), quando è supportato dal cluster; non presumono che Docker Engine sia installato.

## Convertire un'immagine Docker in SIF

Quando la policy del cluster consente di scaricare immagini dal registro, converti l'immagine in un file SIF. Scegli una posizione di storage autorizzata e con spazio sufficiente; per immagini grandi, segui le indicazioni locali sul nodo e sul filesystem da usare.

```bash
apptainer pull python-3.12.sif docker://python:3.12-slim
```

Puoi controllare l'immagine ed eseguire un comando al suo interno:

```bash
apptainer inspect python-3.12.sif
apptainer exec python-3.12.sif python --version
```

Apptainer consiglia di scaricare l'immagine una volta e poi eseguire il file SIF, invece di scaricare nuovamente l'immagine Docker a ogni avvio.

## Usare il container in un job SLURM

Inserisci il comando `apptainer exec` nella sezione di esecuzione del tuo script SLURM, dopo aver richiesto le risorse e la partizione appropriate secondo la [guida ai job](../slurm/jobs.md):

```bash
apptainer exec "$SLURM_SUBMIT_DIR/python-3.12.sif" python train.py
```

L'immagine e i dati devono trovarsi in percorsi leggibili dal job. Controlla le regole del cluster per trasferimenti, scratch e persistenza dei risultati.

## Job GPU

Per un'immagine con librerie CUDA compatibili con i driver del nodo, Apptainer può rendere disponibili i dispositivi e le librerie NVIDIA dell'host con `--nv`:

```bash
apptainer exec --nv /percorso/immagine-cuda.sif nvidia-smi
```

Richiedi anche una risorsa GPU sulla partizione prevista dalle [istruzioni SLURM](../slurm/partitions.md). Verifica con gli amministratori la compatibilità di CUDA, driver e immagine; `--nv` da solo non installa CUDA né assegna una GPU.

## Se hai davvero bisogno di Docker Engine

Docker Engine e l'accesso al suo demone richiedono una configurazione gestita dagli amministratori. Chiedi loro se il servizio è previsto e quale procedura approvata usare. Non aggiungere autonomamente il tuo account a gruppi privilegiati e non avviare servizi Docker sui nodi condivisi.
