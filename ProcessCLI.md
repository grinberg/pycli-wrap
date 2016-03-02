# About ProcessCLI() #

This function provides 90% of functionality. It is the most important because it will be where your program will make things.

# Make my own ProcessCLI() #

You need to pay attention on one thing to replace this function with your own development.

  * ProcessCLI\_dict property

This variable (dict type) contains this by default:

```

    self.ProcessCLI_dict = {
            'help': self.help,
            'dummy': self.dummy,
        }

```

Then, you would have to replace **ProcessCLI\_dict** key-value pairs with your own values-functions. You must consider this:

  * **key** has CLI entry values
  * **value** has a function name, without () characters

You must assign your dict when main class creates the instance. Remember this piece of code:

```
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

Now, we name the new dictionary as **myProcessCLI\_dict** (for example) with these values:


```

    myProcessCLI_dict = {
            'help': myhelpfunction,
            'dummy': mydummyfunction,
        }

```

And assign new dictionary on this way:

```

#NEW CHANGES
myProcessCLI_dict = {
            'help': myhelpfunction,
            'dummy': mydummyfunction,
            'gathersomedata': mynewgathersomedatafunc,
        }

cli = CLIwrap.CLImain()


#NEW CHANGES
cli.ProcessCLI_dict = myProcessCLI_dict 

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

Remember make docstring in "myhelpfunction_" and "mydummyfunction_".