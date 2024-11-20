`ls -al ~/.ssh` — to check SSH keys that have already been generated, if they exist.

`ssh-keygen -t rsa -b 4096 -C` — to generate a pair of SSH keys.

`ssh-add ~/.ssh/id_rsa` — to add a private key to the SSH agent.