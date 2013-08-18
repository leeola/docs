---
title: How to Contribute to Guides
author: leeolayvar
template: guide.jade
sidebar: {
  'Mission Statement': '#mission-statement',
  'What you will need': '#what-you-will-need',
  'Editing': '#editing',
  'Wintersmith Preview': '#wintersmith-installation-and-preview',
}
---


In this guide, we will get a bit meta and talk about how to write guides.
We'll cover the *"Mission Statement"* and the basic process of how to
Fork, Commit, and make a Pull Request on the official Koding Docs repo. Basic
understanding of Git is required, but if there is any confusion on the
Pull Request process hopefully this Guide will help you overcome that.
Beware, this is a long guide, as we cover a lot of general details.

So, lets get started!



## Mission Statement

While the [Koding Docs Wiki][4] is great for general and quickly evolving
data, things can get messy. Keeping guides consistent and stable can be
difficult, as none of the Wiki is really "controlled". Consistency
has to be enforced by reverting bad changes, rather than attempting to always
add positive changes. So, these guides focus on that one aspect that
the Wiki fails at.

The Guides should be guides only. The general rule of thumb would be:
If i make a video to be paired with the Guide, would you want to watch it?
If you submit a table of Keyboard Shortcuts, would you *(or anyone for that
matter)* want to sit and listen to a person list them off in video form?
Probably not. Tutorial guides make sense for ordered instructions, or
something very error prone, but not so much for simple factual data.
Put that on [the Wiki][4].

Lastly, Guides need to relate to Koding somehow. If the issue(s) trying
to be resolved in the guide do not relate to Koding, why is it in these docs?
If you have a wordpress setting that you are confused about, go lookup
the Wordpress documentation. Now, if you have a problem installing wordpress
due to Kodings pre-configured Apache settings, then maybe a guide would
fit quite well on the Koding Docs. Make sense?

We don't mean to come off as controlling, and we would really love your
contribution to these Docs, but control is the core of what separates
the Guides from the Wiki and it is how we expect to preserve quality. :)



## What you will need

### Knowledge

Knowledge of a topic to the extent that you are able to write a clear and
understandable tutorial on it. If applicable, you can even make a video for
it, but otherwise I *(Lee Olayvar)* will do my best to make videos for
all Guides.

### Markdown

Knowledge of the [Markdown Syntax][1]. The guides are all written in
Markdown, and are compiled to HTML with the [Wintersmith][2] project.

### Optional: Wintersmith

The actual site you see [here][0] is a static site compiled by
[Wintersmith][2]. You won't need to compile or anything, but you can install
it if you like. An installation of Wintersmith would allow you to preview
the rendered Markdown as you write, helping ensure formatting is as you expect.
Again, this is entirely optional. As long as your markdown is valid, you don't
need Wintersmith. For instructions on how to install & run Wintersmith,
[see below](#wintersmith-installation-and-preview).



## Editing

Within the project files you will see a folder called `contents`. This
contains markdown and json documents, mostly markdown, that are compiled
into HTML.

To describe how to edit the docs, or to add your own guide, we will go
over each scenario. Editing is pretty simple, so i'll try to be brief.

### Editing an existing document

Pretend you see a typo on the website, how do you find that file in the
Docs source?

Everything in the main site is relative to the `contents/` source folder. So,
`http://koding.github.io/docs/index.html` is `contents/index.md`. Documents
within folders, are also relative. So
`http://koding.github.io/docs/guides/setting-up-ftp/index.html` can be
found at `contents/guides/setting-up-ftp/index.md`. Note how everything after
`docs/` from the website, and `contents/` in the source folder, are the same!


### Creating new documents

So, if we wanted to create a document under
`http://koding.github.io/docs/guides/my-guide/`, we would create a folder
called `contents/guides/my-guide` and put a file in the folder called 
`index.md`. Everything in that markdown file would now be rendered to
`http://koding.github.io/docs/guides/my-guide/index.html`, simple eh?

Images can also be placed in that folder, allowing you to have
images in your guide. Same goes for additional markdown pages! You can do
pretty much anything you need to do :)


### Consistency

Consistency is very important for these guides. So, look for patterns, and
follow them. Don't put a new guide of yours at `contents/my-guide.md` because
all of the other guides are found within `contents/guides/some-guide/index.md`.

Doing things consistently and correctly are the only ways to get your
content submitted to the official site, so *please*, if you are unsure of
something [ask questions][3]!


## Wintersmith Installation and Preview

### Installation

1. Navigate to the docs repo directory and type `npm install`

2. You're done!

### Usage

Wintersmith can be used to preview your project as you write guides.

1. To start, open a terminal which will run the Wintersmith process. If
  you need access to the terminal while running Wintersmith, you can close it
  or simply open a second terminal.

2. Start wintersmith with `npm run-script preview`.

3. Wintersmith is now running on your VM, and you can preview it by going to
  `http://<vm-Number>.<username>.kd.io:8080/docs/`. Note, that Wintersmith's
  preview web server can be a bit picky. It requires the ending `/`.

4. Now simply make edits, and refresh the Wintersmith page to see them
  rendered! Easy eh? :)



## Additional Resources

- [Git - the simple guide][5]




[0]: http://koding.github.io/docs/
[1]: http://daringfireball.net/projects/markdown/
[2]: https://github.com/jnordberg/wintersmith
[3]: https://github.com/koding/docs/issues/new
[4]: https://github.com/koding/docs/wiki
[5]: http://rogerdudler.github.io/git-guide/

