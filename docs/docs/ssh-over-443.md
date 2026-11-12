# SSH over port 443

Some networks block port 22, so `ssh -T git@github.com` hangs while HTTPS still works. GitHub runs an alternate SSH endpoint on 443:

    Host github.com
      HostName ssh.github.com
      Port 443
      User git

Remote URLs stay unchanged, and `ssh -T git@github.com` should greet the account.
