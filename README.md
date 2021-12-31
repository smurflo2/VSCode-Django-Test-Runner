# Differences On This Fork

- Added "python.djangoTestRunner.prefixWithProjectName" setting to optionally disable prefixing method/class/file/app name with the project name
  - e.g. If this test runner runs the command "python ./manage.py **MyProject**.MyApp.ThisFile.ThisClass.ThisMethod" by default, it will run "python ./manage.py MyApp.ThisFile.ThisClass.ThisMethod" if the prefixWithProjectName command is false

## How To Use This Extension

- clone this repo using your preferred git workflow
- `cd {the-newly-cloned-repo}`
- `pnpm install` or `npm install` to install the necessary packages
- `npx vsce package` to build the .vsix file
- Uninstall Django Test Runner extension (if you have it installed already)
- Install this extension [from the vsix file](https://community.particle.io/t/how-to-install-a-vscode-extension-from-a-vsix-file/51014)
  - tl;dr extensions sidebar -> 3 dot menu in the top right -> Install from VSIX... -> select the .vsix file that was just built (likely {the-newly-cloned-repo}/django-test-runner-3.0.3.vsix)

## To Make Changes

- Make changes to the code
- Run `npx vsce package` to rebuild
- Uninstall Django Test Runner extension
- Reinstall from .vsix

# [django-test-runner](https://marketplace.visualstudio.com/items?itemName=Pachwenko.django-test-runner)

Adds support for running Django tests in [Visual Studio Code](https://github.com/microsoft/vscode). Provides shortcuts to run closest method, class, file, app and previous tests. Provides support for Django-Nose in settings.
Draws inspiration from [vscode-django-tests](https://github.com/remik/vscode-django-tests) and [vim-python-test-runner](https://github.com/JarrodCTaylor/vim-python-test-runner).

## Features

Default shortcuts:

```
Run Closest Test Method: cmd+d+m        extension.djangoTestRunner.runMethodTests
Run Closest Test Class:  cmd+d+c        extension.djangoTestRunner.runClassTests
Run Current Test File:   cmd+d+f        extension.djangoTestRunner.runFileTests
Run Current App Tests:   cmd+d+a        extension.djangoTestRunner.runAppTests
Run Previous Tests:      cmd+d+p        extension.djangoTestRunner.runPreviousTests
```

VSCodevim keybindings (put these in your settings.json file):

```
"vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["leader", "d", "m"],
      "commands": ["python.djangoTestRunner.runMethodTests"]
    },
    {
      "before": ["leader", "d", "c"],
      "commands": ["python.djangoTestRunner.runClassTests"]
    },
    {
      "before": ["leader", "d", "f"],
      "commands": ["python.djangoTestRunner.runFileTests"]
    },
    {
      "before": ["leader", "d", "a"],
      "commands": ["python.djangoTestRunner.runAppTests"]
    },
    {
      "before": ["leader", "d", "p"],
      "commands": ["python.djangoTestRunner.runPreviousTests"]
    }
],
```

## Requirements

Requires manage&#46;py to be in the root workspace directory, otherwise add a cd command to the `python.djangoTestRunner.prefixCommand` settings such as "cd ~/Projects/hello-world/src &&"

## Extension Settings

This extension contributes the following settings:

- `python.djangoTestRunner.djangoNose`: if checked will use django-nose syntax for running class/method tests inside a file, defaults to non-nose testing syntax
- `python.djangoTestRunner.flags`: any flags you wish to run such as --nocapture, also useful for specifying different settings if you use a modified manage&#46;py
- `python.djangoTestRunner.prefixCommand`: any command(s) to be directly before the main test command e.g. "cd ~/Projects/hello-world/src &&" to cd into the directory containing your manage&#46;py
- `python.djangoTestRunner.prefixWithProjectName`: optionally disable prefixing method/class/file/app name with the project name
  - e.g. If this test runner runs the command "python ./manage.py **MyProject**.MyApp.ThisFile.ThisClass.ThisMethod" by default, it will run "python ./manage.py MyApp.ThisFile.ThisClass.ThisMethod" if the prefixWithProjectName command is false

## Known Issues

- Default shortcuts may or may not work and require setting them manually

Open a issue/feature request and more at [the github repository](https://github.com/Pachwenko/VSCode-Django-Test-Runner/issues)

## Release Notes

Adds support for running Django Tests a multitude of ways such as by method or class. Supports Django-Nose syntax, test flags, and prefix commands.

### 1.0.0

Initial release of Django Test Runner
