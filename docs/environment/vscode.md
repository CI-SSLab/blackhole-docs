# VS Code sul cluster

L'estensione **Remote - SSH** apre una finestra locale collegata via SSH. Il codice e gli strumenti restano sul cluster; l'interfaccia gira sul tuo computer.

1. Installa Visual Studio Code e l'estensione Microsoft *Remote - SSH*.
2. Aggiungi l'host `blackhole` in `~/.ssh/config` seguendo [la guida SSH](../access/ssh.md).
3. In VS Code apri la palette dei comandi e scegli **Remote-SSH: Connect to Host...** → `blackhole`.
4. Apri la cartella del progetto nella sessione remota.
5. Seleziona l'interprete Python nell'ambiente creato con [uv](uv.md).

Usa Remote - SSH per modifica, ispezione e attività leggere. Per training e calcoli, invia un job SLURM; la sessione editor non sostituisce una prenotazione di risorse.

Se VS Code non rileva la chiave, verifica prima `ssh blackhole` dal terminale. Non incollare chiavi private in VS Code o nella chat.
