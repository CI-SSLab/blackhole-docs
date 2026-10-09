# Partizioni SLURM

SLURM assegna le risorse richieste quando il job entra in esecuzione. Scegli la partizione in base al workload e chiedi al team l'account da associare se necessario.

| Partizione | Risorsa indicata | Uso tipico |
|---|---|---|
| `xcpu` | CPU | preprocessing, simulazioni e calcolo CPU |
| `xgpu1` | GPU NVIDIA RTX 4060 | esperimenti GPU compatibili con la memoria disponibile |
| `xgpu2` | GPU NVIDIA Titan X | esperimenti GPU compatibili con la memoria disponibile |

Richiedi la GPU con `--gres=gpu:1`. Verifica con il team la quantità di RAM, le versioni CUDA, il numero di CPU associato e le eventuali opzioni specifiche della macchina: questa prima guida non presume valori non comunicati.

## Limiti temporali

- **Standard:** massimo `24:00:00` per job.
- **Research:** massimo `7-00:00:00` per job, se autorizzato per il progetto.

Questi sono limiti di durata, non nomi di partizione. Se il cluster usa QoS o account distinti per applicarli, chiedi al responsabile i valori effettivi prima di inviare il job.

## Controlla la coda

```sh
sinfo
squeue --me
```

Per evitare attese, chiedi solo CPU, memoria, GPU e tempo realmente necessari. Se un job supera il limite, SLURM può terminarlo.
