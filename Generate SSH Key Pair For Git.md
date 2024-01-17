Before you start, check if SSH is [[Check If SSH Is Installed|up and running]].

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

Copy the public key to your clipboard:

`$ cat ~/.ssh/git_ed25519.pub | pbcopy  # On macOS`

`$ cat ~/.ssh/git_ed25519.pub | clip     # On Windows with Git Bash`

If you're on Linux without `pbcopy`, you can manually copy the key from `~/.ssh/git_ed25519.pub`.`

# #5. Configure Git to Use the Key for Commits:

Tell Git to use the new key for signing commits:

`$ git config --global user.signingkey "$(ssh-keygen -lf ~/.ssh/git_ed25519.pub -E md5 | awk '{print $2}' | sed 's/://g')"`

Note: On Windows, make sure to use Git Bash for this command.

Now, your new Ed25519 key pair is set up for signing Git commits. Remember to use the `-S` flag when committing to sign the commit, and Git will use this key for signing.

`$ git commit -S -m "Your commit message"`

# #6. Git Hosting Platforms
It's prudent to also add the key to the relevant Git hosting platform you're using (such as GitHub, GitLab, or Bitbucket).

You can do this by going to your Git hosting platform and adding the key in the SSH keys section of your account settings.

## Add Key To Github
Here's how you add your public key to [[How To Update Your GitHub Public Key|GitHub]].