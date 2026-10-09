# Accesso SSH

SSH offre un collegamento cifrato al nodo di login. L'indirizzo reale viene comunicato dal team: `LOGIN_HOST` è un segnaposto da sostituire.

## Crea una chiave (se non ne hai già una)

```sh
ssh-keygen -t ed25519 -C "nome.cognome@istituzione"
```

Proteggi la chiave privata con una passphrase. Condividi con l'amministratore **solo** il contenuto del file pubblico `.pub`; non inviare mai la chiave privata.

## Configura il client

Nel file `~/.ssh/config` del tuo computer, aggiungi:

```sshconfig
Host blackhole
    HostName LOGIN_HOST
    User USERNAME
    IdentityFile ~/.ssh/id_ed25519
    IdentitiesOnly yes
```

Poi connettiti con:

```sh
ssh blackhole
```

Se il cluster richiede VPN o un host intermedio (jump host), chiedi al team i dettagli prima di aggiungerli alla configurazione. Non pubblicare file di configurazione contenenti host interni o nomi utente.

## Copia file

Per trasferimenti puntuali puoi usare `scp` dal tuo computer:

```sh
scp dati.csv blackhole:~/progetto/
scp blackhole:~/progetto/risultati.csv ./
```

Per dataset grandi, concorda con il team il percorso e il metodo di trasferimento appropriati.
