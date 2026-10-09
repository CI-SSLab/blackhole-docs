# SSH access

SSH provides an encrypted connection to the login node. The team provides the actual address; `LOGIN_HOST` is a placeholder to replace.

## Create a key (if you do not already have one)

```sh
ssh-keygen -t ed25519 -C "name.surname@institution"
```

Protect the private key with a passphrase. Share **only** the contents of the public `.pub` file with the administrator; never send the private key.

## Configure your client

Add this to `~/.ssh/config` on your computer:

```sshconfig
Host blackhole
    HostName LOGIN_HOST
    User USERNAME
    IdentityFile ~/.ssh/id_ed25519
    IdentitiesOnly yes
```

Then connect with:

```sh
ssh blackhole
```

If the cluster requires a VPN or a jump host, ask the team for details before adding them to your configuration. Do not publish configuration files containing internal hostnames or usernames.

## Copy files

For occasional transfers, run `scp` from your computer:

```sh
scp data.csv blackhole:~/project/
scp blackhole:~/project/results.csv ./
```

For large datasets, agree on an appropriate path and transfer method with the team.
