---
title: About DevAssistant
page: devassistant
section: tools
description: Lorem ipsum dolor sit amet, consectetur adipiscing elit. In in tristique felis. Duis ornare velit at libero sollicitudin congue. Mauris a pharetra augue. Ut vehicula sed neque sed congue. 
---

# What is DevAssistant

## The Basics

DevAssistant is a tool that helps you start with developing software—for every
project, you need dependencies, a certain file and directory structure, and
often some services or the firewall set up. You no longer need to copy commands
from lengthy tutorials online before developing any web app, library, or a
software tool. Now only one DevAssistant command (or a few clicks in the GUI)
and you are done.  Imagine that running the following command in the command
line:

    $ da create java maven --name MyJavaApp --github

gets you a fully functioning Maven-based Java application with dependencies,
metadata, and a fresh GitHub repository with the code already uploaded. The
same can be said about mostly every major language, because there is an
assistant (a recipe) for that.

## Under the Hood

DevAssistants is essentially an engine that loads and executes scripts called
assistants, one for each workflow you need to cover—the assistants may be tied
to programming languages (e. g. C, Java, Ruby, Python), or generic tasks like
publishing your code to GitHub. There are a few assistants that are maintained
by the DevAssistant upstream developers, and there are more that were created
by the community. In Fedora, you will find mostly the first kind. Do not worry
though, you can easily install community assistants too.

To operate DevAssistant, you can choose from one of the user interfaces:
Currently there is a command-line interface (it will be used throughout this
documentation), and a graphical interface (GUI). Generally speaking, it does not
matter which of them you choose, but at the moment, the DevAssistant developers
have trouble finding time and people to develop and fix the GUI, so using the
command-line interface should get you better and more consistent results.
However, they are currently rewriting DevAssistant to a client-server
architecture, and the existing GUI will soon be replaced by an interface that
runs in your browser.

## Assistants

As said above, the assistants are the scripts that DevAssistants uses to set up
your environment. There are four major roles that the assistants fall into:

* **Create** empty projects – You run a `create` assistant when you want to
  start writing a completely new project, one that isn't existing yet.
* **Tweak** current project – This sort of assistants are run on the code you
  are currently working, be it one that you created with DevAssistant, or
  someone else's. In [Tutorials](#LINK-TO-TUTORIALS), there is a tutorial on
  how to publish your code to GitHub with a `tweak` assistant
* **Prepare** someone's code – As opposed to `create` assistants, `prepare`
  assistants set up code of an existing project for you to contribute to.
  Except for cloning the code from the internet, they install dependencies you
  need for testing the project or create a fork of the original project on
  GitHub.
* **Extra** workflows – In this role, you can find assistants that cover other
  actions you may want to perform on your code, like creating distribution
  packages, validation and verification, and anything else.

For quick illustration, If you want to create a brand new application based on
Django (a Python web framework) which supports Docker containers, you need to
run a command that looks like this (`da` is short for DevAssistant):

    da create python django --name MyAppName --docker

If you want to see how test the application locally, you run the following
command in the project's directory to start the container that was created
along with the app:

    da tweak docker develop

All you need is to point your browser to the address the assistant told you. If
you want to go through a more detailed description of how to do things with
DevAssistant, visit the [tutorials page](#LINK-TO-TUTORIALS).

Except for the assistants written by the developers of DevAssistant, there are
those written by the community, and even you can write assistants for your own
project, or for a language that has not yet been covered by someone else. How
to install assistants is covered [below](#LINK-TO-INSTALLATION)

# Installation

## Installing DevAssistant on Fedora

If you are running Fedora Workstation, there is a good chance that you already
have DevAssistant and the common assistants installed. To check that, try
looking for DevAssistant in your Applications menu, or type `da` into the
command line. If you get something like this, you already have DevAssistant:

    Couldn't parse input, displaying help ...

    You can either run assistants with:
    da [--debug] {create,tweak,prepare,extras} [ASSISTANT [ARGUMENTS]] ...

    Where:
    create   used for creating new projects
    tweak    used for working with existing projects
    prepare  used for preparing environment for upstream projects
    extras   used for performing custom tasks not related to a specific project
    You can shorten "create" to "crt", "tweak" to "twk" and "extras" to "extra".

    Or you can run a custom action:
    da [--debug] [ACTION] [ARGUMENTS]

    Available actions:
    doc      Display documentation for a DAP package.
    help     Print detailed help.
    pkg      Lets you interact with online DAPI service and your local DAP
    packages.
    version  Print version

If you do not see such a message, you can get DevAssistant from GNOME Software,
or install it through DNF:

    $ sudo dnf install devassistant

## Getting New Assistants

Getting DevAssistant the way described above gets you also a common set of
assistants (recipes) for major languages. These assistants are packaged in
Fedora, they get updates when the rest of the system is updated etc. You can,
however, install third party assistants from the [DevAssistant Package Index
(DAPI)](https://dapi.devassistant.org) if they are not available through Fedora
channels. To get the third party assistants, run:

    $ da pkg install PackageName

Where `PackageName` is the name of package you got on the web version of the
DAPI, or found by searching in the command line:

    $ da pkg search KeyWord

Alternatively, you may list all the available packages and choose from that:

    $ da pkg list --available

Installing through `da pkg install` saves the assistants in a hidden folder
(`.devassistant`) inside your home directory, so they are not available to
other users.

