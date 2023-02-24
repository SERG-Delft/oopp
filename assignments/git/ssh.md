---
layout: page
title: Create SSH Keys
parent: Git
grand_parent: Assignments
nav_order: 2
permalink: /assignments/git/ssh
---

# {{ page.title }}

SSH keys are a way to authenticate yourself to another party, for example, for remote terminal access or services like GitLab.
They replace the need for the usual username/password authentication.

The only basic knowledge that you need to know for using SSH keys is that they consist of a *private* part and a *public* part, you will the technical details later in your studies (i.e., in *Security and Cryptography*).
As the name suggests you should _never_ share the private part of your key. That's roughly equivalent to giving someone your password. The _public_ part of your key is meant to be shared with other parties.

In laymen terms, you can encrypt messages with your private key, which can then only be decrypted with your public key, and vice versa.
It is cryptographically hard to reconstruct a *private key* from a *public key*, so only the holder of the private key can see the contents of these messages.

In the following steps you'll create your private and public keys (your keypair) and you'll upload the _public_ part of your key to GitLab so that GitLab will be able to authenticate you.

### Install OpenSSH

First make sure that you have a working OpenSSH installation on your machine.
The installation depends on your concrete operating system.
The following list contains installation guides for the most common operating systems, if you cannot find yours in the list, searching on the internet will likely give you countless examples.

- MacOS/Linux should come with OpenSSH pre-installed.
- [Get started with OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

Us the following command to test whether you have SSH installed:

    ssh -V

This should return something like.

    OpenSSH_8.6p1, LibreSSL 3.3.6


### Creating your SSH key

The SSH application can be used to connect to remote servers.
While this can also be achieved through password authentication, the preferred way of using SSH usually is to use SSH keys, as this is more secure and also eliminates the need for typing in passwords.

By default, the `.ssh` folder inside your home directory is checked for SSH keys.
Keys with a *default name* (like `id_rsa`, `id_ed25519`, etc.) will be picked up automatically.
Advanced users can use different filenames, but this either requires manual loading (using your `ssh-agent`) or editing the SSH config (`~/.ssh/config`).
Further information abotu this can be found in the SSH documentation.

If you do not have a `.ssh` folder or when it is empty, you need to [create an SSH key][gl-create-key].
In teh creation wizard, you can leave the filename empty to use the default and do not set a passphrase for most convenient (albeit less secure) access.
For your first steps, we recommend you to stick with the defaults.
However, we also recommended you though to study the whole [documentation on SSH][gl-ssh] to understand which other options you have.

Once you have generated your keys, you should find a pair of *private* and *public* key in the `.ssh` folder of your home directory (e.g., `id_rsa` and `id_rsa.pub`).

[gl-ssh]: https://docs.gitlab.com/ee/user/ssh.html
[gl-create-key]: https://docs.gitlab.com/ee/user/ssh.html#generate-an-ssh-key-pair


### Using SSH to connect to Git repositories

When you select the *clone* button in a GitLab project, you can pick between URLs for *HTTPS* and *SSH*.
We strongly recommend you to select the SSH option, as this allows you to avoid password authentication altogether.
Instead, the authentication will be based on your newly created SSH keys.

To enable this functionality, you need to [add your public key to your GitLab account][gl-add-key].
Essentially, you need to copy the contents of your *public key file* (e.g., `id_rsa.pub`) and register them in your personal profile: Go to [GitLab](https://gitlab.ewi.tudelft.nl) » Profile Picture (top right) » Preferences » SSH Keys (Left Menu Bar).
When you've completed all steps, you are now allowed to access GitLab via SSH.

[gl-add-key]: https://docs.gitlab.com/ee/ssh/#add-an-ssh-key-to-your-gitlab-account


### Test your connection

To check whether you can successfully connect to GitLab, you can run the following command;

```
ssh -vT git@gitlab.ewi.tudelft.nl
```

This will output something as follows;

```
OpenSSH_8.6p1, LibreSSL 2.8.3
debug1: Reading configuration data /Users/[username]/.ssh/config
debug1: /Users/[username]/.ssh/config line 9: Applying options for gitlab.ewi.tudelft.nl
...
debug1: Connecting to gitlab.ewi.tudelft.nl port 22.
debug1: Connection established.
...
debug1: Authenticating to gitlab.ewi.tudelft.nl:22 as 'git'
...
debug1: Will attempt key: [path to your private key and some more details]
...
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: [path to your private key and some more details]
debug1: Server accepts key: [path to your private key and some more details]
debug1: Authentication succeeded (publickey).
Authenticated to gitlab.ewi.tudelft.nl ([131.180.119.16]:22).
...
Welcome to GitLab, @[username]!
...
```


### Use SSH with graphical Git clients

All popular, graphical Git clients support connecting via SSH.
The concrete setup depends on the application that you use.
The following list contains instructions for tools that we recommend.

- [GitKraken](https://www.gitkraken.com/learn/git/problems/github-add-ssh-key#) (Ignore all GitHub references in this Guide)
- [Git Tower](https://www.git-tower.com/help/guides/manage-hosting-services/manage-ssh-keys/windows)
- [Sourcetree](https://support.atlassian.com/bitbucket-cloud/docs/set-up-ssh-with-sourcetree/) (Be careful with incorrect password! Sourcetree will automatically retry, which can get you banned at our GitLab server)




