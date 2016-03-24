# dotgit
## A simple bash program to store and manage all your dotfiles (multiple hosts) in a single git repo

Using dotgit will allow you to effortlessly store all your dotfiles in a single git repo. Dotgit doesn't only do storage - it also manages your dotfiles between multiple computers and devices. It has the ability to keep multiple versions of the same file (example different vimrcs) in the same repo, but it also allows you to easily share the same file between two or more devices (like a bashrc). It also incorporates an easy-to-use category system, so you can group a bunch of dotfiles together and keep them in-sync and versioned.

This makes the following situation possible:

Say you have a vimrc that you prefer to share between a laptop and a desktop (with the terribly original hostnames `laptop` and `desktop`) but you also have a Raspberry Pi where you prefer to keep another vimrc (with the hostname `pi`). There's also a .bashrc that you'd like to share between all three and a .foo file that you would like to have only on all of your servers. After initializing a folder with "dotgit init" you could edit the filelist too look like this:

```
.vimrc:desktop,laptop -- Will share the file between the two and keep them synced
.vimrc:pi -- Will be unique to the pi
.bashrc -- Will be shared between every device that shares this repo, regardless of hostname (unless a category is used)
.foo:server -- Will only be linked into the home folder if you use the category server
```
Simply running `dotgit update` in your dotgit repo would set up (a quite complex) symlinking hierarchy and link all the files into your home directory. Restoring all your symlinks from the repository is just as simple. Run `dotgit restore` and all the files that are relevant to the host will be symlinked into your home folder.

Dotgit also:
* Generates commit messages
* Automatically push the repo to a remote
* Supports files that reside in folders (like .scripts/backup.sh)
* Supports spaces in filnames \0/
* Print a help message (awesome feature :P)

It's written in bash so its easy to set up and use :) If you have any questions or feature requests please feel free to request them!

## Installation
[AUR Package](https://aur.archlinux.org/packages/dotgit)

If you are running a different distro you can just copy the dotgit script over to your local bin folder and it will run happily :) (Any help with packaging for a different distro will be appreciated)

## Instructions
Remember that this is simply a git repo so all the usual git tricks work perfectly :)
There are two way to start up a repo: First is to create your online repo, clone it and then run `dotgit init` (alias for `git init` and creating a file and folder needed for dotgit) in it or you can simply make an empty dir, run `dotgit init` inside of it and then `dotgit add-remote "repo url"`.

Now all you have to do is edit the filelist (help message explains syntax) to your needs and you will be ready to do `dotgit update` :) The help message will explain the other options available to you, and I would recommend reading it as it has quite a few important notes. Have a good one
