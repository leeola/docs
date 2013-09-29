---
title: Using Tmux
author: leeolayvar
template: guide.jade
sidebar: {
  'Odd Behavior': '#odd-behavior',
  'The Solution': '#the-solution',
  'But i love C-b!': '#but-i-love-c-b!'
}
---

In this Tmux FAQ we will address an issue people have had with Tmux on Koding.
It's easy to deal with, but not an obvious workaround.

## Odd Behavior

When you first try and install and run tmux on Koding, it seems to load
load properly, but many commands just don't seem to work. Some, like `C-b c`
*(used to create a new window)* even force close the Terminal. What is going
on?

Well, Koding uses GNU Screen to help reconnect your Terminal sessions after
connection issues. Koding's preconfigured Screen is set to use `C-b` as it's
own prefix key. So when you run and use Tmux, and attempt to use `C-b`
commands, you are actually sending commands to Screen. This explains the
general odd behavior, as things like `C-b c` in Screen mean "close",
so you unintentionally logout of screen and close your Terminal.

## The Solution

The solution is quite simple, rebind your Tmux Prefix key. This can be
done by creating a `~/.tmux.conf` file and placing the following command
into it:

```
set-option -g prefix C-a
```

Where `C-a` is Control *key*. This sets it to Control-a, a popular alternative
for Tmux users *(and the traditional Screen PREFIX)*. You can of course bind
it to whatever you want. Once you have your PREFIX rebound, killall tmux
instances and reopen, and it will run just like you expect.. just remember
to use Control-a as your PREFIX :)

## But i love C-b!

Unfortunately, this is the way it has to be for now. A guru developer over at
Koding did mention that they would like to make their version of screen 
not use any keybinds, so that it does not block your input at all. So, think
of this alternate bind as a short-term workaround, until this "issue" is
resolved.

