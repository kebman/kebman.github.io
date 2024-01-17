# Generate SSH Key Pair For Git
Before you start, check if SSH is [up and running](Check If SSH Is Installed.md).

Use the following steps to generate a *specific* key for signing Git commits.

# #1. Open a Terminal/Command Prompt:

   - If you're on Linux or macOS, use the terminal.
   - If you're on Windows, you can use Git Bash or the Command Prompt.

# #2. Generate the Ed25519 Key Pair:

Run the following command, replacing the email with the one associated with your Git account:

`$ ssh-keygen -t ed25519 -C "your_email@example.com" -f ~/.ssh/git_ed25519`

This command generates a new Ed25519 key pair and saves it in the `~/.ssh/` directory with the filename `git_ed25519`.

# #3. Add the New SSH Key to the SSH Agent:

Start the SSH agent if it's not already running:

`$ eval "$(ssh-agent -s)"`

Add the new private key to the SSH agent:

`$ ssh-add ~/.ssh/git_ed25519`

# #4. Configure Git to Use the New Key:

`$ git config --global gpg.format ssh`

# #5. Specify Which Key To Use

`$ git config --global user.signingkey ~/.ssh/git_ed25519.pub`

Now, your new Ed25519 key pair is set up for signing Git commits. Remember to use the `-S` flag when committing to sign the commit, and Git will use this key for signing.

`$ git commit -S -m "Your commit message"`

Note: If you don't want to use the -S flag every time you commit, make signing default with this line:

`$ git config --global commit.gpgsign true`

# #6. Git Hosting Platforms
It's prudent to also add the key to the relevant Git hosting platform you're using (such as GitHub, GitLab, or Bitbucket).

You can do this by going to your Git hosting platform and adding the key in the SSH keys section of your account settings.

## Add Key To Github
Here's how you add your public key to [GitHub](How To Update Your GitHub Public Key.md).
