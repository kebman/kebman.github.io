Before you start, check if SSH is [[Check If SSH Is Installed|up and running]].

If you don't have any private or public signing keys, you'll have to use SSH to generate a new pair.

Note: It might be better to make a [[Generate SSH Key Pair For Git|specific]] key pair for Git, however.

# Read Before Running

When you run the command for generating the key pair, you'll be prompted to enter a file to save the key. Press Enter to accept the default location, or provide a custom path.

Next, you must set a passphrase for added security. Make sure it has at least four words.

The key pair will be generated, and you'll see output indicating the key fingerprint and location.

# Generate A New Key Pair

Here's the command for generating a new SSH key pair:

`$ ssh-keygen -t ed25519`

Congrats, You've successfully generated a new Ed25519 SSH key pair!

The private key is saved in the specified file, and the public key is saved with the same filename but with a `.pub` extension.

You'll need to enter your passphrase whenever you use the private key.

# Important
Don't ever share the private key. Keep it private under all circumstances.

