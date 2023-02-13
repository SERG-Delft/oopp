---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

# [Link button](http://example.com/){: .btn .btn-tud }

layout: page
title: Set up SSH keys
parent: Git
grand_parent: Assignments
nav_order: 3
permalink: /assignments/git/ssh-keys
---

# Set up SSH Keys
SSH keys are a way to authenticate yourself to another party (for example a service like GitLab). They replace the need for the usual username/password authentication. You'll learn more about this once you follow a course on Security and Cryptography. For now, you should only remember that SSH keys consist of a **private** part and a **public** part. As the name suggests you should _never_ share the private part of your key. That's roughly equivalent to giving someone your password. The _public_ part of your key is meant to be shared with other parties. Using the public part of the key anyone can send secure messages your way. Only when you have the private key then you can see the contents of these messages. In the following steps you'll create your private and public keys (your keypair) and you'll upload the _public_ part of your key to GitLab so that GitLab will be able to authenticate you.

## Creating your SSH key
When you first open your new GitLab account, it will give you a notification that you have not set up an SSH key yet. To make cloning easier we will start off by creating a SSH key. GitLab has an easy to follow tutorial on both [creating the key][gl-create-key]. Note that in the tutorial you come across a step where you can set a passphrase for your (private) key. It's not required to do so. When you set a phrase, then make sure to remember it, as you'll be asked for the phrase every time you want to load/use your key. When you set no passphrase then you should ensure that nobody can access the private key file on your device (use a strong password to login and don't leave your device unlocked/unattended).

## Uploading your public key to GitLab
The tutorial on GitLab also contains a part on [adding your public key to your GitLab account][gl-add-key]. When you've completed all steps your private key is now allowed to access the GitLab instance.

## Where are my keys? 

By default, the `.ssh` folder inside your home directory is checked for SSH keys. Use a default default name for the keys (like `id_rsa`, `id_ed25519`, etc.) so the keys can be picked up automatically.

Advanced users can also use a different filenames, but this either requires manual loading (using your `ssh-agent`) or editing the SSH config (`~/.ssh/config`).
If you want to go this route, you can find further information in the SSH documentation.

## Test your connection

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
```

[gl-create-key]: https://docs.gitlab.com/ee/ssh/#see-if-you-have-an-existing-ssh-key-pair
[gl-add-key]: https://docs.gitlab.com/ee/ssh/#add-an-ssh-key-to-your-gitlab-account

When you want to use your generated key with GitKraken, then you need to add it first. By default the key is stored in your user folder in a folder called `.ssh`.

> <a href="{{site.baseurl}}/assets/images/gitkraken/select-generated-ssh-keys.png" data-lightbox="gitkraken-select-generated-ssh-keys" data-title="Select already generated SSH keys.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/select-generated-ssh-keys.png" />
> </a>

If you do not have any keys, you can generate them.

> <a href="{{site.baseurl}}/assets/images/gitkraken/generate-ssh-key.png" data-lightbox="gitkraken-generate-ssh-key" data-title="Generate private/public key.">
>    <img src="{{site.baseurl}}/assets/images/gitkraken/generate-ssh-key.png" />
> </a>