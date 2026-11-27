# Signing commits with an SSH key

Git can sign commits with the same SSH key used for authentication, so a separate GPG
setup is not needed:

    git config --global gpg.format ssh
    git config --global user.signingkey ~/.ssh/id_ed25519_hpkt3285.pub
    git config --global commit.gpgsign true

The key also has to be added on GitHub as a **signing key**. A key that only has the
authentication role still lets pushes through, but the commits stay unverified.

To check signatures locally, put the public key in an allowed signers file and point Git
at it:

    git config --global gpg.ssh.allowedSignersFile ~/.ssh/allowed_signers
    git log --show-signature -1

On Windows, forward slashes in `user.signingkey` avoid backslash escaping problems in the
config file.
