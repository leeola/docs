---
title: SSH Into Your VM
author: leeolayvar
contributors: [gemmalynn]
template: guide.jade
sidebar: {
  'Video': '#video',
  'What you will need': '#what-you-will-need',
  'Tutorial Steps for OpenSSH on Linux': '#tutorial-steps-for-openssh-on-linux',
  'Tutorial Steps for PuTTY on Windows': '#tutorial-steps-for-putty-on-windows',
  'Possible Gotchas': '#possible-gotchas',
  'Confirming your Installation': '#confirming-your-installation',
  'Additional resources': '#additional-resources'
}
---


In this tutorial, we will go over the steps to SSHing into your VM! This
is a semi-experimental tutorial, so if you have any problems please make
sure to
[submit an issue][1]
and we can help make this a rock solid tutorial for all skill levels :)

**Reminder**: As with all of these tutorials, they assume that there are no
conflicts. If you have previously attempted to install this software please
remove it fully or understand that conflicts may occur. Thanks :)




## Video

### Linux Video

<iframe width="680" height="450" src="//www.youtube.com/embed/9tsmL61HgXU" frameborder="0" allowfullscreen></iframe>

### PuTTY Video

<iframe width="680" height="450" src="//www.youtube.com/embed/hngKOMVptvU" frameborder="0" allowfullscreen></iframe>




## What you will need

In this tutorial, I am going to use the terminology of "Home" and "Koding"
machines. Home being whatever the machine you are using to connect to
Koding with. Koding being the machine that is receiving the connection.
`Home -> Koding`.

On the Home machine, you will need your SSH public/private keys. On Linux (or
Cygwin on Windows), your SSH keys are usually found at `~/.ssh/id_rsa` and
`~/.ssh/id_rsa.pub`. On Windows (without Cygwin), you may need to generate new
keys with
[PuTTYGen](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html). If
you need to generate a new key pair, please refer to a
[Linux](https://help.github.com/articles/generating-ssh-keys) or
[Windows](http://katsande.com/using-puttygen-to-generate-ssh-private-public-keys)
tutorial, as appropriate.  You will also need your Koding Username, and your VM
Number.

To find your VM number, review the [Find your VM Number][0] guide.




## Tutorial Steps for OpenSSH on Linux

1. First, copy your Public Key, usually found in `~/.ssh/id_rsa.pub`, and copy
  it in its entirety! It will look something like this:
  
  ```
  ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCyhKankDE4DRM86JqZ3JPdWDeqg+TbzlqlTLf
  OKTeokhRoMgy5WoMY/ZWUVES3d2vSHHwW3cwWlELmVdc3Ow57boZv3fOsPhybYHVRTClXYr1ncS
  xyTvjvCfvV5q22aIxHPWQ353543ssda87sa+85XEa4VnveJsEzxBZl4oJ4GB0AGa48+UdIqutrg
  Zu7D7JCK+Yl228X+3bJf3ddlqDaKaVXPivvvYqImK6ZwFsxh2lNO4E8IOd3OSK9zv6i+io8PxWm
  wP0tLFokxulAI8Td1sOPBE9s9bdJ5c2T/GfGjKF+aNKsd33TsYEjjc/plMZmRRrOgQwre6OAkgM
  vyV2X foo@bar.baz
  ```
  
2. Next, paste this entire Public Key into your SSH Keys section of your
  Account settings. This can be found by going to
  [Koding/Account](https://koding.com/Account) and clicking SSH Keys
  under the DEVELOP. Click the Plus button on the right side of the page,
  and paste your Public Key into this. Below is a screenshot of this area
  for clarification.
  ![Koding SSH Keys](sshkeys.png)
  
3. Now go back to your Home machine, and create the file
  `~/.ssh/config` *(assuming it's not already created)*. Add the following
  code into that file:
  
  ```
  Host *.kd.io
    User <username>
    ProxyCommand ssh %r@ssh.koding.com nc %h %p
  ```
  
  Where `<username>` is your username, without the `<>`.
  
4. Next, on your Home machine and connect to your VM! This can be
  done by typing: `ssh <vm-Number>.<username>.koding.kd.io`. An example,
  here is my connection command: `ssh vm-0.leeolayvar.koding.kd.io`.
  
  You will have to enter your local SSH password, if you chose one when you
  created your key. After that, presented with `username@vm-X:~$`, signaling
  that you have connected successfully.
  
  This step has quite a few Gotchas so please review them below.
  
  Two likely gotchas, are
  [Possible Gotchas: Agent Failure](#agent-admitted-failure?)
  and
  [Possible Gotchas: ssh_exchange_identification](#ssh_exchange_identification-/-keep-koding-open-in-browser)
  below.
  
  ### Error: Could not chdir
  
  This "error" can be ignored. I'm not sure what exactly causes it, but
  everyone experiences it and it does not cause any problems.
  [@kiwigeraint](https://koding.com/kiwigeraint) says to simply ignore it. :)





## Tutorial Steps for PuTTY on Windows

For this connection method, you will need the [PuTTY SSH client suite][10]:
`putty.exe`, `plink.exe`, and `pageant.exe`.

**Note:** This PuTTY guide has only recently been published. If you are
familiar with PuTTY and you think something should be changed, please
[let me know][1]!

1. Copy the text contents of your PuTTY public key. If you are not sure what or
  where it is, please refer to [What you will need](#what-you-will-need).

2. As in Step #2 of the [Linux guide](#tutorial-steps-for-openssh-on-linux)
  above, paste the entirety of your public key into the _SSH Keys_ section of
  your Koding account settings.

3. Start up `putty.exe` and set the _Host Name (or IP address)_ to the same VM
  hostname as above:
  
  `vm-Number.<username>.koding.kd.io`
  
  ![PuTTY session](puttysession.png)

4. In the _Category_ menu on the left, select _Data_ under _Connection_. Enter
  your Koding username in the _Auto-login username_ box.

5. Select _Proxy_ under _Connection_, and change the _Proxy type_ to _Local_.
  Enter the following line (modified for your system) in the _Telnet command,
  or local proxy command_ box:
  
  `C:\your\path\to\plink.exe <username>@ssh.koding.com -nc %host:%port`
  
  ![PuTTY proxy](puttyproxy.png)

6. Go back up to the *"Session"* settings and save this PuTTY
  configuration to a new session by typing a name into the *"Saved Sessions"*
  box, and clicking on *"Save"*.

7. In Step 7, we will cover setting up your Auth. This can be done two
  ways, and we will cover both. **You only need to do one** method!
  Pageant has been working for everyone, where as PuTTY-Auth has been
  a bit problematic but is shorter. Choose whichever you like, but if you
  have issues, try [Pageant Auth](#pageant-auth).
  
  ### Pageant Auth
  
  Open `pageant.exe`. It will launch into your Taskbar.
  
  ![Pageant Taskbar](pageanttaskbar.png)
  
  Right click the Pageant icon in the taskbar, and select *"View Keys"*. From
  there, click the *"Add Key"* button. Navigate to your PuTTYGen **private**
  key and click *"Open"*. You should now have a key listed in your Pageant Key
  List. An example image is below.
  
  ![Pageant key List](pageantkeylist.png)
  
  If your key has been added to the Pageant Key List, close the window.
  
  ### PuTTY Auth
  
  Reopen PuTTY and select your Session, then click Load.
  
  Next, under the _Connection_ menu, open up the _SSH_ menu and select _Auth_.
  Enable the _Allow agent forwarding_ checkbox. Under _Private key file for
  authentication_, browse to your PuTTYGen private key.
  
  ![PuTTY SSH auth](puttyauth.png)
  
  Next, Plink needs to know the explicit location of your key. So go back to
  *"Proxy"* under *"Connection"* and look for the *"Telnet command,
  or local proxy command"* box. Currently, it should look like this:
  
  `C:\your\path\to\plink.exe <username>@ssh.koding.com -nc %host:%port`
  
  Modify it, by adding your private key location. So, it will look like
  this:
  
  `C:\your\path\to\plink.exe -i c:\path\to\private\key.ppk <username>@ssh.koding.com -nc %host:%port`
  
8. You're done! You can now connect to Koding via PuTTY.

  To connect with Pageant, you can right click the Pageant
  Icon, and under *"Saved Sessions"* click on your Saved Session. This
  will automatically open up PuTTY and start connecting.
  
  To connect from PuTTY itself, open PuTTY and select your Saved Session from
  the list, then click Open.
  
  An example of a successful Koding Connection is below.
  
  ![Success](puttysuccess.png)


### Troubleshooting

If you have trouble connecting, try running the Plink proxy command in `verbose`
mode (`-v`) from a console (outside PuTTY itself). You'll need to manually specify the
private key with `-i`.

`> C:\path\to\plink.exe -v -i c:\path\to\private\key.ppk <username>@ssh.koding.com -nc vm-Number.<username>.koding.kd.io:22`

If it ends with a line resembling `SSH-2.0-OpenSSH_5.9p1` then your connection
should be good, and the problem is likely elsewhere.

## Confirming your Installation

The best way to confirm your installation is simply by connecting to your
Koding VM. For information on this, see Step #3 above.




## Possible Gotchas


### Agent admitted failure?

If you receive an error when you attempt to connect, matching the following
description:

```
Agent admitted failure to sign using the key.
```

Then run the command `ssh-add`. For additional information on this gotcha,
see the
[Github Help Page](https://help.github.com/articles/error-agent-admitted-failure-to-sign)
on the subject.



### ssh_exchange_identification / Keep Koding Open in Browser

Until Always-On VMs are available, Koding will shut down your VM after
approximately ~20 minutes. To ensure that you are able to connect properly
make sure you have your browser open **and logged in** to Koding.com.

If you experience the following error:

```
ssh_exchange_identification: Connection closed by remote host
```

Your VM being "off" is the most likely culprit. You can ensure it is on by
visiting its direct url, such as http://vm-0.username.kd.io, and ensuring
you are presented with your Hello World Apache response. If you receive
an error indicating that VM does not exist or is not on, you should have a
good idea why SSH is failing to connect.

If your VM is toggled off, it can be turned on by going to
[koding/Develop](https://koding.com/Develop) and looking for your VM under
**Your Environments**, in the lower left. An image is below for reference:
![Make sure VM is ON](onvm.png)



### ~/.ssh/authorized_keys

You do *not* need to use authorized_keys in the Koding VMs. The
Account Settings -> SSH Keys takes care of the authorization for you.



## Additional Resources

- [Agent Failure Information](https://help.github.com/articles/error-agent-admitted-failure-to-sign)




[0]: /docs/guides/find-your-vm-number/
[1]: https://github.com/koding/docs/issues/new

[10]: http://www.chiark.greenend.org.uk/~sgtatham/putty/
[11]: http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html


