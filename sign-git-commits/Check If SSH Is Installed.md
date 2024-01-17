# Check If SSH Is Installed
Before you start, you need to check if SSH is up and running.

Note: If you're on Windows, use Git Bash for all the Linux-like commands instead of PowerShell or Command Prompt.

## Check if ~/.ssh/ exists

`$ ls -la ~\.ssh`

## Check if SSH is even installed
If the above folder doesn't exist, then you may need to install Open SSH.

Check if SSH is running first:

- Windows PowerShell: `$ Get-Service -Name sshd`
- Windows PowerShell: `$ Get-Process sshd`
- Linux: `$ sudo systemctl status ssh`
- OS X: `$ sudo systemsetup -getremotelogin`
- Linux / OS X Daemon: `ps aux | grep sshd`

If SSH isn't installed, then check an installation guide relevant to the OS you're using, and then install it.

## Check if any SSH-keys exists
Check if you have any public keys:

`$ ls -la ~\.ssh\*.pub`

If there are no keys, you'll have to generate a [new key pair](Generate SSH Key Pair.md).

### Note
Even if you have an existing key, you may still want to generate a new key pair [just for signing commits](Generate SSH Key Pair For Git.md). The reason is because it lowers exposure and thus hypothetical risk.
