---
title: About DevAssistant
page: devassistant
section: tools
description: Lorem ipsum dolor sit amet, consectetur adipiscing elit. In in tristique felis. Duis ornare velit at libero sollicitudin congue. Mauris a pharetra augue. Ut vehicula sed neque sed congue. 
---

# What is DevAssistant

DevAssistant is a tool that helps you start with developing software—for every
project, you need dependencies, a certain file and directory structure, and
often some services or the firewall set up. You no longer need to copy commands from
lengthy tutorials online for each and every web app, library, or a tool you
write. Now you only run one DevAssistant command and you are done. Imagine that
running the following command in the command line:

    $ da create java maven --name MyJavaApp --github

gets you a fully functioning Maven-based Java application with dependencies,
metadata, and a fresh GitHub repository with the code already uploaded. The
same can be said about mostly every major language, because there is an
assistant (a recipe) for that. Aside from the command-line version, you can
also use the DevAssistant GUI, but for reasons explained [below](#GUI), we
recommend you do not.

# Installation

## DevAssistant

If you are running Fedora Workstation, there is a good chance that you already
have DevAssistant and the common assistants installed. To check that, try
looking for DevAssistant in your Applications menu, or type `da` into the
command line. If you get something like this:

    $ da
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

That means that you have DevAssistant on your machine, and you can skip the
rest of this chapter and go to Tutorials. If not, you can get DevAssistant from
GNOME Software, or install it through DNF:

    $ sudo dnf install devassistant

## Assistants

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

# Some Notes

## Further Reading

The tutorials and information found here are targeted mainly at beginners, so
if you are interested in more in-depth reading, feel free to check out the
following sites.

* [DevAssistant Homepage](https://www.devassistant.org)
* [DevAssistant User Documentation](http://doc.devassistant.org/en/latest/user_documentation.html)
* [DevAssistant Blog](https://blog.devassistant.org)
* [DevAssistant Developer Documentation](http://doc.devassistant.org/en/latest/developer_documentation.html)

## GUI

DevAssistant is currently undergoing a major overhaul, so the current GUI is
old and will eventually be replaced. We recommend using the command-line
interface for the time being.
