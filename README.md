
# Getting started with ArrowOS

![ArrowOS](https://github.com/ArrowOS/getting_started/blob/master/etc/logo.png?raw=true)

[https://www.arrowos.net/](https://www.arrowos.net/)

## Feedbacks, reporting or contacting us

**Email us at:** [arrowos.contact@gmail.com](arrowos.contact@gmail.com)

**Telegram Channel:**
http://t.me/Arrow_OS
**Telegram Group:**
http://t.me/ArrowOS

Syncing ArrowOS source
---------------
To get started with the ArrowOS sources, you'll need to get
familiar with [Git and Repo](https://source.android.com/setup/build/downloading).

To initialize your local repository, use command:

```bash
    repo init -u https://github.com/ArrowOS/android_manifest.git -b arrow-9.x
```

Then sync up:

```bash
    repo sync  -f --force-sync --no-clone-bundle -jX
```
Where X is the thread your CPU can handle.

Building the System
-------------------
 Initialize the ROM environment with the envsetup.sh script. By using the following command

     . build/envsetup.sh
     brunch device-codename


**Refer here for more:** https://blog.arrowos.net/posts/compilation-guide

## Posting on XDA, or any other Forum.
Basically follow the below thread template or something closer to this

**Thread Template:** [Click here](https://github.com/ArrowOS/getting_started/blob/master/thread_template.txt)


## Applying for Official status
**You can apply for the maintainership by mailing us at** [arrowos.contact@gmail.com](arrowos.contact@gmail.com)

**Be sure to include** : 

* Your name
* GitHub, Telegram and XDA usernames.
* Link to device tree, kernel source and vendor source.
* Device name, codename.
* What's working, what's not working and do mention SeLinux status
* Attach two screenshots, one of About section in Settings of the ROM and the other of terminal on build complete.
* Please release the build to public (in forums like XDA, 4pda or your device's forum) before you apply or send an email for OFFICIAL status

**Refer here for more** https://blog.arrowos.net/posts/apply-for-maintainership

## Contributing

You can contribute and push patches to our Gerrit/Codereview where we will review the changes and merge if needed, but hey every single contribution counts! :))

Sign up on our gerrit [review.arrowos.net](https://review.arrowos.net/) using either a google account or github account and set a **USERNAME** in profile section.

-   Open your local terminal and generate a ssh key by running the following command. Refer this  [guide](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)  for more info on how to generate ssh keys.

```bash
ssh-keygen
```

-   Now add the contents of your ssh public key(~/.ssh/id_rsa.pub) to your gerrit account in the SSH Public Keys section.

```bash
#This command will print out all the contents of your public key file
cat ~/.ssh/id_rsa.pub
```

-   Once done adding the ssh key to your gerrit account you may run the following command to check the connection with gerrit.

```bash
ssh -p 29418 USERNAME@review.arrowos.net
```

If everything went well you’ll be greeted with a welcome message that the connection has been established. If you receive any error saying “**permission denied(public key)**”, that means your SSH keys aren’t entered correctly, try repeating STEP 2 again.  
In this case it is better to start things from scratch by removing your old ssh keys with the following command.

```bash
rm -rf ~/.ssh
```

Once you have verified your SSH keys and a successful connection with gerrit, you’re ready to submit patches.

##### Below is an example showing how to submit a commit to  **android_vendor_arrow**  repo on ArrowOS gerrit:

This example commit shows you how to add a device to official list.

From the root of your source:

```bash
cd vendor/arrow/
```

Now make your changes, i.e. here we edit the  **arrow.devices**  file to add the device codename and build type.  
Once you have finished doing the changes

```bash
git add .
git commit -m "vendor: added xyz device to official"
```

This will generate a commit with the changes you have made.

##### Now to push the changes:

```bash
git push ssh://USERNAME@review.arrowos.net:29418/ArrowOS/android_vendor_arrow HEAD:refs/for/arrow-8.x
```

Here  **android_vendor_arrow**  is the repository name and arrow-8.x is the branch, change them accordingly to the repo and branch you’re trying to push to.

**If you get an error about missing change-ids**

```bash
curl -Lo .git/hooks/commit-msg http://review.arrowos.net/tools/hooks/commit-msg

chmod u+x .git/hooks/commit-msg
```

**Refer here for more** : [https://blog.arrowos.net/posts/gerrit-guide](https://blog.arrowos.net/posts/gerrit-guide)
