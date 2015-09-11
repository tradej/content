---
title: DevAssistant Tutorial
page: devassistant
order: 1
---

Assuming you have DevAssistant and the assistants installed, let's try out
kickstarting the development with some concrete examples in various languages.
Mind you that each language has different needs, so the assistants for Python
look a little different than those for Perl.

In these tutorials, we'll use the command-line interface, but the usage of the
GUI is identical. However, at the moment, we discourage using the GUI for these
reasons.

## Getting started with Flask

Flask is a lightweight but robust Python web server, and it's perfect for creating a
simple, mostly static home page. If you want something bigger, you can try
Django—we've got an assistant for that too.

Let's go through some steps to find out how you can create and customize the
project:

    da create python flask --help

Running the above command gives you a message that looks like this:

    usage: create python flask [-h] [--venv] [-e [ECLIPSE]] [-g [GITHUB]] -n NAME [-r] [-v]

    Flask assistant will help you create a basic Flask project and install its
    dependencies.

    optional arguments:
    -h, --help            show this help message and exit
    --venv                Use virtualenv to set up project and install
                          dependencies.
    -e [ECLIPSE], --eclipse [ECLIPSE]
                          Configure as Eclipse project (uses ~/workspace or
                          specified directory)
    -g [GITHUB], --github [GITHUB]
                          Create a GitHub repository and push your sources there
                          (uses your system username or specified name)
    -n NAME, --name NAME  Name of project to create
    -r, --rpm             This will create SPEC file and install dependencies
                          for building RPM package.
    -v, --vim             Configure VIM editor for various programming languages

Let's pretend you want to name your Flask app "MyFancyWebserver" and want to
publish the sources on GitHub. As you can figure out from the help message
above, you'll have to run the following command:

    da create python flask --name MyFancyWebserver --github UserName

That's a bit long, isn't it? You can write it in a much shorter way, especially
if your GitHub username is the same as that on your local machine:

    da crt python flask -n MyFancyWebserver -g

When you run that, DevAssistant does all the magic for you—installs
dependencies, creates files and directories and more:

    [UserName@localhost]$ da crt python flask -n MyFancyWebserver -g
    INFO: Resolving RPM dependencies with DNF...
    Installing 2 RPM packages with DNF. Is this ok? [y(es)/n(o)/s(how)]: s
    python-flask-wtf-0.10.0-2.fc22.noarch
    python-wtforms-2.0-4.fc22.noarch
    Installing 2 RPM packages with DNF. Is this ok? [y(es)/n(o)/s(how)]: y
    Installing dependencies ........... Done.
    INFO: Creating Flask project MyFancyWebserver in . ...
    INFO: Registering your project on GitHub as UserName/MyFancyWebserver...
    INFO: Your new repository: https://github.com/UserName/MyFancyWebserver
    INFO: Adding Github repo as git remote ...
    INFO: Successfully added Github repo as git remote.
    INFO: Source code was successfully pushed.
    INFO: Flask project MyFancyWebserver in . has been created.
    INFO: To run the application use: ./manage.py runserver
    INFO: For more information about Flask project visit https://flask.pocoo.org/docs/tutorial/
    [UserName@localhost]$ 

As you can see, DevAssistant allows you to verify which packages are installed.
During the run of the assistant, you may be asked for the administrator (root)
password several times, especially when dependencies are being installed.
