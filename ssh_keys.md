
https://superuser.com/questions/232373/how-to-tell-git-which-private-key-to-use



In ~/.ssh/config, add:

Host github.com
 HostName github.com
 IdentityFile ~/.ssh/id_rsa_github

If the config file is new, you might need to do chmod 600 ~/.ssh/config

Now you can do git clone git@github.com:{ORG_NAME}/{REPO_NAME}.git

    Where {ORG_NAME} is your GitHub user account (or organization account)'s GitHub URI name.
        Note that there is a colon : after github.com instead of the slash / - as this is not a URI.
    And {REPO_NAME} is your GitHub repo's URI name
    For example, for the Linux kernel this would be git clone git@github.com:torvalds/linux.git).

NOTE: On Linux and macOS, verify that the permissions on your IdentityFile are 400. SSH will reject, in a not clearly explicit manner, SSH keys that are too readable. It will just look like a credential rejection. The solution, in this case, is:

chmod 400 ~/.ssh/id_rsa_github

