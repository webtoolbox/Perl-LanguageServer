**Usefuls:**

- \<SSH_USERNAME\>: replace with your ssh_username i.e: rishabh,
- \<SERVER\>: replace with your server i.e: beta36

# SSH Login with keys (Workspace Terminal)

- cd ~/.ssh
- ssh-keygen -t ed25519 -C "`<SSH_USERNAME>`"
- **Ask to enter key name:** `<SERVER>`
- **Ask to enter paraphrase:** do not enter any paraphrase, press enter to skip, same for confirm paraphrase
- chmod 0600 `~/.ssh/<SERVER>`
- chmod 0644 `~/.ssh/<SERVER>.pub`
- ssh-copy-id -i `~/.ssh/<SERVER>.pub` `<SSH_USERNAME>@<SERVER>.websitetoolbox.com`
- eval \``ssh-agent -s`\`
- **Connect with key:** ssh -v -i `~/.ssh/<SERVER>` `<SSH_USERNAME>@<SERVER>.websitetoolbox.com`
- On asking for password, ask `Masihur Sir` to allow login with public key.

## WTBX Perl Extension Setup Steps

- Open VS Code,
- Press `CTRL + SHIFT + p`, then type settings.json, then click on `open user settings json`
- add following lines within json 
    ```
    {
        ...,
        "perl.sshAddr": "<SERVER>.websitetoolbox.com",
        "perl.sshUser": "<USERNAME>",
        "perl.sshWorkspaceRoot": "/www",
        "perl.sshPort": "22",
        "perl.sshCmd": "ssh",
        "perl.sshArgs": [
            "-i",
            "~/.ssh/<SERVER>",
            "-A"
        ],
        "perl.perlCmd": "sudo -u www-data /etc/langServer.sh"
        
    }
    ```
- Press `CTRL + SHIFT + X` to open extension panel,
- Search for `Perl` extension by `Gerald Richter` and uninstall it, if already installed,
- Click on `three dots` at the top right corner of the extension panel,
- Click on `Install from VSIX`, then type `/wttransfer` on search bar (where path is shown),
- Open `wtbx-perl-0.0.1.vsix`, if not found, ask `Masihur Sir` to upload it.
- And all set.
