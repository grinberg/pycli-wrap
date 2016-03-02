[![](http://pycli-wrap.googlecode.com/files/pyCLI-enter.jpg)](http://pycli-wrap.googlecode.com/)

This project is a wrapper for any other program developed in Python. It provides an extra feature to them.

You can adapt quickly any Python program to have a command line interface (CLI). This CLI can reuse any function that you have already developed.

Also, It uses Python Docstring Conventions PEP 257(http://www.python.org/dev/peps/pep-0257/) inside of your class methods or functions to build CLI help.

It supports:

  * Windows and Linux.
  * Python version: > 2.5.x

# News #

  * 21 Sep 2011 Version 0.0.0 released.

# Downloads #

  * [pycli-wrap-0.0.0.tgz](http://code.google.com/p/pycli-wrap/downloads/detail?name=pycli-wrap-0.0.0.tgz) - Full functional

# Features #

**Features v.0.0.0**

  * Support Windows and Linux
  * Support Python 2.5 or later
  * Customize the prompt string
  * Customize the function which control tasks running in real time. See_InfiniteLoopTasks_
  * Customize CleanUp actions, when you want exit of the program.
  * Customize task which run when user press "Enter"
  * Customize key codes to launch your own actions.

# Things we are working on #

We are working in tasks to make more easy the code. The next goal is provide more quickly adaptation of our you for your code of easy way.

Also we want to provide you more examples and extend the official documentation.

# Usage #

We need "clirt-example.py" file to understand the explanation. The content is:

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import os
import sys

#check operating system
if os.name == 'posix':
    from lib import CLIposix as CLIwrap
elif os.name == 'nt':
    from lib import CLInt as CLIwrap
else:
    print "Error: current OS not supported ;)"
    sys.exit(0)
      
cli = CLIwrap.CLImain()

configure_dict = {
    'PromptStr': "myCLI> ",
    'InitialTasks': cli.InitialTasks,
    'PressEnterTasks': cli.PressEnterTasks,
    'CleanUpTasks': cli.CleanUpTasks,
    'InfiniteLoopTasks': cli.InfiniteLoopTasks,
    'ProcessCLI': cli.ProcessCLI,
    'EnterKeys': cli.EnterKeys,
    'ExitWords': cli.ExitWords,
    'ExitKeys': cli.ExitKeys,
}

cli.configure(**(configure_dict))
cli.run()

```

You can use this file to adapt any program that you already have. Now, I am going to explain which parts you could customize.

**configure\_dict dict() {}**

```

configure_dict = {
    'PromptStr': "myCLI> ",
    'InitialTasks': cli.InitialTasks,
    'PressEnterTasks': cli.PressEnterTasks,
    'CleanUpTasks': cli.CleanUpTasks,
    'InfiniteLoopTasks': cli.InfiniteLoopTasks,
    'ProcessCLI': cli.ProcessCLI,
    'EnterKeys': cli.EnterKeys,
    'ExitWords': cli.ExitWords,
    'ExitKeys': cli.ExitKeys,
}

```

---

Every dictionary key is optional. If you need only one or several options, you must create the dict() which contains selected 'keys' to customize **pycli**.

Now, I am going to explain each option:

  * **PromptStr**: String with cli prompt. e.g: c:\ # $
> > Default: "myCLI> "


> Pay attention to leave one white space at the end of the string.

  * **InitialTasks**: Function with tasks which run once. At loop begining.
> > Default: Show this banner:

###################################
# Welcome to CLI Python Prototype #
###################################

  * **PressEnterTasks**: Function with tasks which run when user press 'Enter' key or defined by **EnterKeys** (see later).
> > Default: Show current date/time.

  * **CleanUpTasks**: Function with task which run when exit of the loop, it means exit of execution.
> > Default: Print "Exiting..." string.

  * **InfiniteLoopTasks**: Functions with task which run infinite times, on every loop cycle. I recommend small task or threaded tasks.
> > Default: Nothing.

  * **[ProcessCLI](ProcessCLI.md)**: Function which process 'words' written on the CLI prompt and when you press 'Enter'.
> > Default: It accepts 'help' and 'dummy' words.

  * **EnterKeys**: Function which defines the Keys which responds as 'Enter Key'.
> > Default: `<CR`> `<LF`> `<CTRL`>+D

  * **ExitWords**: Function which defines the words which gives exit of the execution when you press 'Enter'.
> > Default: 'exit', 'salir', 'quit'

  * **ExitKeys**: Function which defines the Keys which gives exit of the execution
> > Default: `<CTRL`>+C `<CTRL`>+D



# Development #

If you want to colaborate on this project, contact with us.
