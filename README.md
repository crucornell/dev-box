CruCornell Development Box
==========================

Apparently a lot of people run Windows, which was making life difficult.
This development box quickly and easily spins up a virtual machine with
Ruby, Jekyll, Git, and other things necessary to do development on
crucornell.com, all without having to navigate the shifting landscape of
build tools necessary to install everything directly.

Working this way also has the advantage that you can't really break your
development environment. If you mess up, just tear it down and start
over.

Getting Started
---------------

1. Somehow get these dev-box files somewhere on your system. If you know
   git, run `git clone https://github.com/crucornell/dev-box.git`, but
   you can also just download a zip file
   [from here](https://github.com/crucornell/dev-box/archive/master.zip).
   I'm going to assume you've called this directory "dev-box".
2. Somehow get
   [the crucornell website](https://github.com/crucornell/crucornell.github.com)
   _into that new dev-box directory_ (like, right next to Vagrantfile).
   One good way to do that, especially if you're unfamiliar with git, is
   to use [GitHub for Windows](http://windows.github.com/), and tell it
   to clone the repository right into the middle of the dev-box directory.
   You're doing this because that directory will be shared between your
   computer and the VM we're creating. You want to be able to edit files
   and whatnot from both. I'm going to assume you've cloned the crucornell
   website code into a folder called "crucornell-cod"e inside the dev-box
   directory.
3. Download and install [Vagrant](http://downloads.vagrantup.com)
4. Download and install [VirtualBox](http://www.virtualbox.org/wiki/Downloads)
5. Pop open a terminal window wherever you put the dev-box Vagrantfile.
6. Run `vagrant up`, which will download the virtual machine image (first
   time only), and boot it up (this will take a while).
7. Once it's up, run `vagrant ssh` to connect a shell to it for running
   commands inside the VM. The following commands will be run in this shell.
8. Run `cd /vagrant/crucornell-code`, and then run `jekyll serve --watch`.
9. Now open up a web browser on your computer and [click here](http://localhost:4000).
   Pretty slick, eh?

When you're done with your VM, you can exit the ssh session (`exit`), and
then run `vagrant destroy`. Next time you just do `vagrant up` from the
dev-box directory, `vagrant ssh`, and you'll be able to get back to work
again from `/vagrant/crucornell-code`.
