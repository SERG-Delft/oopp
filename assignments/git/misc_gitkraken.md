---
layout: page
permalink: /git-assignment/install-gitkraken
parent: Git
grand_parent: Assignments
---
# Install GitKraken

{: .info }
As a student at TU Delft you are eligible for [GitHub's Student Pack](https://education.github.com/pack). As part of this pack you get access to a free [Pro license for GitKraken](https://www.gitkraken.com/github-student-developer-pack).

Install the application as you would install any other application, afterwards start GitKraken. Authenticate with GitHub (if you want to make use of your acquired Student benefits through the education pack). You should create a profile, give it a name you like (for example "TU Delft") and enter **your full name** and **student email address**.

{: .important }
Make sure you configure the email address and full name properly. Course staff uses scripts to run automated analyses of the repositories. We use this information to identify you/your work.

<a href="{{site.baseurl}}/assets/images/gitkraken/first-start.png" data-lightbox="gitkraken-first" data-title="Create a GitKraken profile.">
    <img src="{{site.baseurl}}/assets/images/gitkraken/first-start.png" />
</a>

You now see the homescreen of GitKraken where you can start a new repository, or where you can clone (download) an existing project. You can connect your GitKraken client to EEMCS' self-hosted GitLab instance, or you can clone projects one by one via their URL (either works fine).

<a href="{{site.baseurl}}/assets/images/gitkraken/homescreen.png" data-lightbox="gitkraken-home" data-title="GitKraken home screen.">
    <img src="{{site.baseurl}}/assets/images/gitkraken/homescreen.png" />
</a>

When you click "Clone a repo" you will get the following menu.

<a href="{{site.baseurl}}/assets/images/gitkraken/init-self-hosted-gitlab.png" data-lightbox="gitkraken-init-gitlab-self-hosted" data-title="Connect GitKraken to EEMCS' GitLab instance.">
    <img src="{{site.baseurl}}/assets/images/gitkraken/init-self-hosted-gitlab.png" />
</a>

To connect to EEMCS' GitLab instance you need to use the following details;

- Host domain: `gitlab.ewi.tudelft.nl`
- Personal Access Token: generate one in your [GitLab Profile settings](https://gitlab.ewi.tudelft.nl/-/profile/personal_access_tokens) with scopes `api` and `read_user`.

<a href="{{site.baseurl}}/assets/images/gitkraken/enter-details-self-hosted.png" data-lightbox="gitkraken-details-self-hosted" data-title="Details to connect to EEMCS' GitLab instance.">
    <img src="{{site.baseurl}}/assets/images/gitkraken/enter-details-self-hosted.png" />
</a>

Next, go to the Preferences, and visit the SSH Keys tab to check the settings there. In case you have already generated SSH keys that you'd like to use then you can select your public and private keys here. GitKraken will then use these keys to authenticate towards GitLab. There's also an option to create a keypair in case you had not done so yet.

<a href="{{site.baseurl}}/assets/images/gitkraken/ssh-settings.png" data-lightbox="gitkraken-ssh-settings" data-title="Details to connect to EEMCS' GitLab instance.">
    <img src="{{site.baseurl}}/assets/images/gitkraken/ssh-settings.png" />
</a>

You should now have a functioning GitKraken client on your device. Remember, that if you want to work on multiple devices that you have to repeat the process for these devices too. In terms of your SSH keypair you have two options;

- Copy your private/public key to all devices where you need to authenticate to GitLab,
- Create a new keypair on the other device, and add the public key to your GitLab profile.

{: .info }
Ideally you use unique keys everwhere. This reduces the risk of having to replace all yours keys when your keypair gets stolen/leaks. This is a decision you have to make for each situation. Working for a bank? You want to be extra careful and preferably use different keypairs. Working on a project for university? Then it's typically fine to just copy your keys. 🙂

When GitKraken is configured you can continue the Git Assignment with [the `git clone` operation]({{site.baseurl}}/git-assignment/clone).