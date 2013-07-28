---
title: Koding Overview
author: leeolayvar
template: guide.jade
---



Koding offers nearly unlimited possibilities; so many infact, that people
often misunderstand what Koding is being designed for. Knowing the goals
of the platform will help you make the most of it and not feel misled when
something isn't as expected.

This guide will briefly go over what Koding is, identify some
misconceptions people have, and why certain restrictions and choices were
made.



## What Is Koding?

Koding is an online development environment with the goal of simpifying
wordwide development and providing free computation and development to
everyone.

It does this by offering Free VMs for development to anyone.
The Koding VMs provide you with a *real* Ubuntu OS, with a *real* Terminal,
and allow you to work on *real* code. Python, PHP, C++, C, it doesn't matter.
Even better, they are online. Accessible from anywhere in the world. Even
sharable with teams.



## Is Koding a Production Host?

Koding is first and foremost a Development Environment. All features have been
tailored with this in mind and evidence of this is reflected in all of the
features you see implemented. Lets highlight some of these items.

### VMs Shutdown After Logout

Approximately 20 minutes after you log out, your Free VMs will shut down. Why?
Koding's development focus is not centered around hosting a your blog/site.
Koding is here to enable you and to help you make great things. Attempting
to be yet another host in a sea of perfectly capable production hosts
won't help achieve that goal.

**Note:** In the future Paid Always-On VMs will be an option. This is
currently not available though.

### CPU Bursts vs Sustained

The VMs are designed in such a way that they help short processes complete
fast, but less so to long running processes. Why? Well, you have to admit
that giving everyone 100% CPU all the time for a free host is unrealistic.

Production hosts solve this problem by giving you a smaller percentage
of the raw CPU, but at a sustained rate. They offer some burst, but less
burst is generally available due to a more consistent sustained
expectation.

On the otherhand, Koding wants to help you get work done, and get work
done fast. Things like compilers have a lot to compute but in short
sporadic bursts. Koding's CPU allocation has been tailored with this
in mind. It wants you to compute what you need, as soon as possible.
It is not tailored for a long running process that expects heavy
and consistent usage, such as a Minecraft server.

### Raw Ubuntu OS

These days a lot of hosting platforms are heavily optimized for
their specific niche(s). They streamline the process of hosting your
language or application style of choice, which gives you added
stability and performance gains. Examples of this are the plethora
of Apache-PHP hosts, Nodejitsu, Google App Engine, Heroku, AppFog,
and a nearly limitless amount of others.

Why is this? Well, production hosting is hard, and there are obvious
benefits to letting someone else do it. The idea of uploading your
php site to a standard php host is easy. The idea of buying a
dedicated server, setting up Apache, firewalls, updates, etc, just
seems a bit crazy in comparison. Ontop of that, what about
load balancing and CDNs? Doing it all yourself can be hard.

Well, Koding gives you that raw machine. It's not trying to make
production hosting for you, but rather it's giving you a completely
open and powerful environment to *make stuff*! So by all means
*make* your Wordpress blog on Koding, and if you really want
to host it on Koding wait a while and buy an Always-On VM. Just
be aware of the design goals.

