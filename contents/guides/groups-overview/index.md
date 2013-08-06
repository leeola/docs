---
title: Koding Groups Overview
author: leeolayvar
contributors: [andygold]
template: guide.jade
---


Koding Groups are a core feature of Koding, and allow for a lot of versatility
in group programming. It allows your development and team communication
to be in one area, and even sharing the same machines if you use Shared
VMs.

This guide will go over the concepts of Koding Groups, and how to manage
one.



## What are Groups?

Koding Groups basically give you your own corner of Koding. They let you
have you own Activity feed, to discuss anything, with all the features of
the main Koding group. Tags, content types, VMs, etc.

They give you and your team a section of Koding to be productive. The
activity feed of your group can be public or private and you can even make
[Shared VMs](#shared-vms)!

Koding groups are being designed for any number of users. Your team,
your class, your school or your company, anything will fit into a
Koding group.




## Group Dashboard

Your Group Dashboard is the control center for your Group. It contains
settings, invitations and permissions.

To find this, go to your Group, and look in the lower left near Your Account.
Above the Logout button, is a **Group** button. Click this, and you will be
in your dashboard. Settings, invitations, permissions, all of these can
be navigated on the left.



## Shared VMs

Shared VMs are similar to Personal VMs, except that multiple users are on the
same VM. Usage and resources are shared, but locations are not by default.

### Filesystem

The filesystem is a point of confusion for a lot of users. A user will often
expect to be sharing the same home directory as another user. which
is not the case by default.
It is the same machine, but not the same home/user directories.

For the sake of this explanation, lets say we have two users. `john` and
`henry`, with a Shared VM of `shared-0.ourgroup.kd.io`.
In the filesystem, Johns home directory is located at `/home/john`
and Henrys is located at `/home/henry`. The actual `ourgroup` VM is located
at `/home/ourgroup`.

This seems pretty straight forward, but then the next common question is
how can i connect to my Shared VM `~/Web` directory? In a shared VM, 
`~/Web` directories are linked to `/home/<groupname>/Web/~<username>/`.

So, in practice the connection addresses look like this:

- `http://shared-0.ourgroup.kd.io` = `/home/ourgroup/Web`
- `http://shared-0.ourgroup.kd.io/~john` = `/home/john/Web`
- `http://shared-0.ourgroup.kd.io/~henry` = `/home/henry/Web`



## Group Invitations

Since groups can be private, you have multiple methods of inviting team
members. The different ways you can invite are in place to support many
different types of teams.

Invitation settings can be found from your
[Group Dashboard](#group-dashboard) and clicking on **Invitations**.



## Group Settings

Group Settings offer basic customization of a group. You can modify a groups
name, description, readme, and listed & visibility settings.

### Privacy Options

Privacy has two options, Public and Private. This setting just controls
a users ability to request an invite. Nothing more.

So, if Privacy is set to `Public`, users can join themselves by pressing
*"Join"*. If set to `Private`, users must request access by pressing the
*"Request Access"* button.

**Note:** A Privacy setting of `Private` does not mean a random guest/member
cannot view your Group. If you want to make your group unlisted and
content invisible, remove the `Read Activity` permission from the "Guest"
role. Also, see the visibility options below.

### Visibility Options

Visiblity controls whether or not your Group will be listed in the main
Group List and if content posted to your Group will also show up in the
main Koding Feed.

A setting of `visible` means that your group *will* show up in the group list
and all content posted to your group will stream into the main Koding Feed.

A setting of `hidden` means that your group will *not* show up in the
Group List and content will not show up in the Koding Feed.





## Group Permissions

Permissions are quite an extensive topic. In this guide we will focus
on generally explaining Roles, Permissions, and how to assign them to
users.

### Roles

Roles are given a set of permissions, such as read activity and read posts,
and assigned to users of your Group. Allowing you to control what users with
that role are able to do. Groups come with four roles by default, and can
have additional roles added.

To add a role, look for the **Add Role** button in the lower left of the
permissions section.

### Permissions

Permissions are assigned to roles, and then roles to users. Assigning a
permission is quite simple, just check the box for that role. If that role
has a checked box on a permission, then that role has that permission.

For a table with the known permissions described, check out [this wiki
post][1]

Currently we will not go over all of the permissions, but in the future when
more are implemented, as quite a few are not currently, we will put them
in a table here and a video will be dedicated to them.


### Assigning a Role

To assign a role, from your [Group Dashboard](#group-dashboard) hover
over the user you want to assign a role to, and click **Edit**.
From there, check the Role box of the role you wish to grant/deny.

It's worth noting that the **Guest** and **Member** roles are automatically
assigned/removed by Koding.





[0]: https://github.com/koding/docs/wiki
[1]: https://github.com/koding/docs/wiki/Group-Permissions
