CruCornell Development Box
==========================

Apparently a lot of people run Windows, which was making life difficult.  This
development box quickly and easily spins up a virtual machine with Ruby,
Jekyll, Git, and other things necessary to do development on crucornell.com,
all without having to navigate the shifting landscape of build tools necessary
to install everything directly. In the end, you'll use your own machine only to
edit text files.

Working this way also has the advantage that you can't really break your
development environment. If you mess up, just tear it down and start over.

Getting Started
---------------

1. Somehow get these dev-box files somewhere on your system. The easiest way to
   do this is to just download the zip file [from
   here](https://github.com/crucornell/dev-box/archive/master.zip) and extract
   it somewhere. When it comes out, the directory will be called
   "dev-box-master".
2. Somehow get [the crucornell
   website](https://github.com/crucornell/crucornell.github.com) _into that new
   dev-box-master directory_ (like, right next to Vagrantfile).  One good way
   to do that, especially if you're unfamiliar with git, is to use [GitHub for
   Windows](http://windows.github.com/), and tell it to clone the repository
   right into the middle of dev-box-master.  You're doing this because
   whichever folder Vagrantfile is in will be shared between your computer and
   the VM we're creating. You want to be able to edit files and whatnot from
   both your computer and the VM. I'm going to assume you've cloned the
   crucornell website code into a directory called "crucornell-code" inside
   dev-box-master.
3. Download and install [VirtualBox](http://www.virtualbox.org/wiki/Downloads)
4. Download and install [Vagrant](http://downloads.vagrantup.com)
5. Pop open a terminal window and navigate into dev-box-master.
6. Run `vagrant up`, which will download the virtual machine image (first time
   only), and boot it up (this will take a while).
7. Once it's up, run `vagrant ssh` to connect a shell to it for running
   commands inside the VM. The following commands will be run in this shell.
8. Run `cd /vagrant/crucornell-code`, and then run `jekyll serve --watch`.
9. Now open up a web browser on your computer and [click
   here](http://localhost:4000).  Pretty slick, eh?

When you're done with your VM, you can exit the ssh session (`exit`), and then
run `vagrant destroy`. Next time you just do `vagrant up` from the dev-box
directory, `vagrant ssh`, and you'll be able to get back to work again from
`/vagrant/crucornell-code` inside the VM via the SSH session.

When the VM is running, it's also possible to open the VirtualBox Manager from
the Start menu and suspend and resume the VM, or take snapshots. This is
frequently a lot faster than using `vagrant up` to rebuild the VM every time.

Development Workflow
--------------------

1. Resume the VM from VirtualBox Manager or run `vagrant up` to rebuild it.
2. On your own machine, run GitHub for Windows and update crucornell-code.
3. Run `vagrant ssh` to connect to the running VM, and navigate to the
   crucornell-code directory inside the VM with `cd /vagrant/crucornell-code`.
4. Run `jekyll serve --watch` inside the VM to start a server at
   http://localhost:4000 that recompiles the site whenever you save changes to
   any crucornell-code files.
5. On your own machine, use whatever text editor you want to edit the site
   files inside dev-box-master/crucornell-code. Changes should be immediately
   reflected inside the VM, and thus at localhost:4000.
6. When you've made a change you want to keep, use GitHub for Windows to commit
   and push your code to GitHub.
