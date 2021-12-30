---
layout: post
title:  "Configuring VSCode for Python Development"
date:   2021-11-30 00:00:00 +0000
---

## Intro

Many Python software projects enforce a particular code style, lint code with a particular linter etc. Having your editor run these checks in real-time while you're writing can speed up development by catching bugs early, and reducing the amount of refactoring you have to do later.

Here we'll go through an opinionated way to configure [VSCode](https://code.visualstudio.com/) for Python development. We'll assume that your project uses the following:

- `black` [for formatting](https://black.readthedocs.io/en/stable/index.html)
- `flake8` [for linting](https://flake8.pycqa.org/en/latest/)
- `isort` [for import sorting](https://pycqa.github.io/isort/)
- `mypy` [for static type checking](https://mypy.readthedocs.io/en/stable/)

We'll also assume that:

- you have a virtual environment activated with the above tools installed
- the project you're developing in has already configured these tools to work in a particular way via configuration files (like `pyproject.toml`)

We'll run through configuring VSCode to use each of these tools one-by-one while explaining what each setting does, before tying everything up into a neatly organised little settings config at the end. [Skip to the end](#tidying-up) if that's all you're here for 👀.

## VSCode Settings

The easiest way to edit settings in VSCode for a specific software projects is by creating a `settings.json` file at the root of the project. This means you can easily keep hold of the settings incase you change machine etc.

1. `cd` into your project
2. Run `ls -a .vscode/` and see if you already have a `settings.json`
3. If you don't, or get some error suggesting `.vscode/` doesn't exist, then:
   - `mkdir .vscode`
   - `touch .vscode/settings.json`

📝 [Relevant VSCode Docs](https://code.visualstudio.com/docs/getstarted/settings)

## Interpreter

1. Run `which python` in your terminal to get the path to the Python interpreter at the top of your `PATH`
2. Open VSCode from your terminal with `code .`
3. VSCode will attempt to find the correct Python interpreter to use. You can check whether this has worked by clicking on the button with `Python 3.x.x 64-bit` written on it in the bottom status bar, and checking the selected interpreter matches the one from step `2`. If it doesn't, then select the correct one.
4. To help VSCode select the correct interpreter in future when it opens the workspace for your project, set a default interpreter by adding the following to the project's `.vscode/settings.json` file:

```json
"python.defaultInterpreterPath": "path/to/python/from/step/1"
```

📝 [Relevant VSCode Docs](https://code.visualstudio.com/docs/python/environments)

## Formatting

1. Run `which black` in your terminal to get the path to `black` in your virtual environment
2. Add the following to your project's `.vscode/settings.json` file:

    ```json
    "editor.formatOnSave": true,
    "editor.formatOnType": true,
    "python.formatting.provider": "black",
    "python.formatting.blackPath": "path/to/black/from/step/1",
    ```

3. If you want, you can add a vertical ruler to your editor at projects maximum line length - I find this helps quite a bit when writing and re-sizing windows correctly (change the values to your faves):

    ```json
    "editor.rulers": [79],
    "workbench.colorCustomizations": {
        "editorRuler.foreground": "your-fave-hex-value"
    },
    ```

📝 [Relevant VSCode Docs](https://code.visualstudio.com/docs/python/editing)

## Linting

1. Run `which flake8` in your terminal to get the path to `flake8` in your virtual environment
2. Add the following to your project's `.vscode/settings.json` file:

    ```json
    "python.linting.enabled": true,
    "python.linting.flake8Enabled": true,
    "python.linting.flake8Path": "path/to/flake8/from/step/1",
    ```

📝 [Relevant VSCode Docs](https://code.visualstudio.com/docs/python/linting)

## Import Sorting

1. Run `which isort` in your terminal to get the path to `isort` in your virtual environment
2. Add the following to your project's `.vscode/settings.json` file:

    ```json
    "python.sortImports.path": "path/to/isort/from/step/1",
    "[python]": {
        "editor.codeActionsOnSave": {
            "source.organizeImports": true
        }
    }
    ```

📝 [Relevant VSCode Docs](https://code.visualstudio.com/docs/python/editing)

## Static Type Checking

1. Run `which mypy` in your terminal to get the path to `mypy` in your virtual environment
2. Add the following to your project's `.vscode/settings.json` file:

    ```json
    "python.linting.mypyEnabled": true,
    "python.linting.mypyPath": "path/to/mypy/from/step/1",
    ```

📝 [Relevant VSCode Docs](https://code.visualstudio.com/docs/python/linting#_mypy)

## Tidying Up

After a bit of tidying up and re-ordering, you can end up with something like this:

```json
{
    "editor.formatOnSave": true,
    "editor.formatOnType": true,
    "editor.rulers": [79],
    "workbench.colorCustomizations": {
        "editorRuler.foreground": "your-fave-hex-value"
    },
    "python.defaultInterpreterPath": "path/to/virtualenv/python",
    "python.formatting.provider": "black",
    "python.formatting.blackPath": "path/to/virtualenv/black",
    "python.linting.enabled": true,
    "python.linting.flake8Enabled": true,
    "python.linting.flake8Path": "path/to/virtualenv/flake8",
    "python.sortImports.path": "path/to/virtualenv/isort",
    "[python]": {
        "editor.codeActionsOnSave": {
        "source.organizeImports": true
        }
    },
    "python.linting.mypyEnabled": true,
    "python.linting.mypyPath": "path/to/virtualenv/mypy"
}
```

Violà! Your editor should now be configured to format, lint, sort, and type check as you write 🎉. You can copy this `settings.json` file into other projects as needed (though you'll need to change the paths to point at the tool's in that project's virtual environment).
