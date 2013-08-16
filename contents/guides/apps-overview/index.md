---
title: Koding Apps Overview
author: leeolayvar
template: guide.jade
sidebar: {
  'Video': '#video',
  'What are Koding Apps?': '#what-are-koding-apps?',
  'Apps, The nitty gritty details': '#apps,-the-nitty-gritty-details',
  'App Development': '#app-development',
  'App Submission': '#app-submission'
}
---


This guide goes over some useful details regarding Koding Apps. What they are,
how to use them, and how to fix a broken install. We will not go over
App Creation at this time, but there will be a guide for that in the future!



## Video

*(None yet, coming soon!)*



## What are Koding Apps?

Think of Koding Apps like Desktop Applications, on Koding. They can be
anything from simple shortcuts such as installing PureFTPd or MySQL,
to complicated apps such as real Image Editing and Realtime Collaboration.

### Installing Apps

Installation is quite simple. Navigate to [koding/Apps][0] and find the app
you want. Click on the desired app, and click the green **"Install Now"**
button under the App title.

In a moment, once the App installs, you will be directed to
[koding/Develop][1] which shows a list of your installed Apps. To use one,
simple click on it!

Each app will be different, but generally if it's an installer like
PureFTPd, it will have an install option in the upper right. If it's an
app that you use, just click on it and use it :D



## Apps, The nitty gritty details

So, what *are* Apps you ask? Are they run on the server? Are they run on the
client? It's kind of important to know if you want to develop them right?

Koding Apps are basically clientside Apps that use the Koding Framework
to communicate with your VM. This means that potentially any web based
and modular html/js/css app can be turned into a Koding App with some
love! You can see this in the Koding Text editor. It's basically just the
Ace Editor wrapped in the Koding Framework.

So keep an eye out for cool web platforms, chances are good that in
the future we can integrate it into Koding!



## App Development

There are no published api docs currently, which makes development a bit
hard. There are however, two Apps designed to help you develop Koding Apps.
[Kodepad][2] and [Appmaker][3]. It's mostly just code examples, but it's the
best we currently have.

In the future, when i understand App Development more, i'll be making a
guide on the subject. Feel free to [contact me][4] if you'd like to
contribute :)



## App Submission

So, you made an awesome app and you want to submit it right? You can read up 
on the process for basic app submission [here](http://koding.github.io/docs/guides/app-submission/).




[0]: https://koding.com/Apps
[1]: https://koding.com/Develop
[2]: https://koding.com/Apps/kodepad
[3]: https://koding.com/Apps/appmaker
[4]: https://github.com/koding/docs/issues/new

