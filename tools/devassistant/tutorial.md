---
title: DevAssistant Tutorial
page: devassistant
order: 1
---

Assuming you have DevAssistant and the assistants installed, let us try out
kickstarting the development with some concrete examples in various languages.
Mind you that each language has different needs, so the assistants for Python
look a little different than those for Perl.


## The Basics

To launch DevAssistant, either run the `da` (or `da-gui` for the GUI) binaries,
or find DevAssistant in your Applications menu. In these tutorials, we will use
the command-line `da` binary, but the usage of the GUI is very much the same.
However, at the moment, we discourage using the GUI for these reasons.

If you are unsure what assistant to run, you can use the `--help` or `-h` flag,
like this, or use the bash completion with the `TAB` key. You can add `--help`
at any time to see what assistants and options are available:

    $ da --help
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
    pkg      Lets you interact with online DAPI service and your local DAP packages.
    version  Print version

To find more about creating projects, you can run `da create --help`:

    $ da create --help
    usage:  create [-h] [--deps-only] {c,cpp,dap,java,nodejs,nulecule,perl,php,python,ruby} ...

    Kickstart new projects easily with DevAssistant.

    optional arguments:
    -h, --help            show this help message and exit
    --deps-only           Only install dependencies

    subassistants:
      Following subassistants will help you with setting up your project.

      {c,cpp,dap,java,nodejs,nulecule,perl,php,python,ruby}

The above help message lists available assistants used for creating projects,
so you can choose one to try out. For this tutorial, we will go with one of Python
assistants—Flask.

    $ da create python --help
    usage: create python [-h] {django,flask,gtk3,lib} ...

    This is base Python assistant. You have to choose a specific project type.

    optional arguments:
    -h, --help            show this help message and exit

    subassistants:
      Following subassistants will help you with setting up your project.

    {django,flask,gtk3,lib}


## Getting Started with Flask

Flask is a lightweight but robust Python web server, and it is perfect for
creating a simple, mostly static home pages. If you want something bigger, you
can try Django—we have got an assistant for that too.

First, let us display the help message for Flask to find out how you can create
and customize the project:

    $ da create python flask --help
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

Say that you want to name your Flask app `MyFancyWebserver` and want to publish
the source code on GitHub. As you can figure out from the help message above,
you will have to run the following command:

    $ da create python flask --name MyFancyWebserver --github UserName

That is a bit long, is it not? You can write it in a much shorter way,
especially if your GitHub username is the same as that on your local machine:

    $ da crt python flask -n MyFancyWebserver -g

When you run that, DevAssistant does all the magic for you—installs
dependencies, creates files and directories, and more:

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

As you can see, DevAssistant allows you to verify which packages are about to
be installed.  During the run of the assistant, you may be asked for the
administrator (root) password several times, especially during dependencies
installation. After the run is finished, you can see that the directory
`MyFancyWebserver` now exists, and that it is populated with files
automatically:

    $ tree MyFancyWebserver
    MyFancyWebserver/
    ├── application
    ├── httpd.MyFancyWebserver.conf
    ├── LICENSE
    ├── manage.py
    └── MyFancyWebserver
        ├── __init__.py
        ├── static
        │   └── style.css
        └── templates
            └── index.html

    3 directories, 7 files

You can then go to the directory and run `./manage.py runserver` as advised in
the DevAssistant log. You now have a fully functioning webserver after running
a single command in DevAssistant, and can start editing it with your favourite
editor.
