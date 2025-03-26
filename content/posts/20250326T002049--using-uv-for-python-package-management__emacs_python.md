+++
title = "Using uv for python package management"
author = ["Kaushal Bundel"]
date = 2025-03-26T00:20:00+05:30
lastmod = 2025-03-27T01:54:08+05:30
tags = ["python", "Emacs", "programming"]
categories = ["programming"]
draft = false
+++

## What is UV? {#what-is-uv}

-   An fast python package manager and project manager (Written in Rust)
-   replaces pip, pyvenv, virtualenv etc.
-   Runs scripts
-   Installs and Manages Python versions


## Installation {#installation}

-   UV can be installed using any one of the package managers (homebrew, pacman etc)


## Commands {#commands}


### Initializing a project {#initializing-a-project}

```bash
uv init <project_name>
```

-   The above command creates a folder named &lt;project_name&gt;. Inside the project name there is a complete project directory including the virtual environment. UV expects you to follow this project structure.
    -   Project Structure:

<!--listend-->

```text
.
├── .venv
│   ├── bin
│   ├── lib
│   └── pyvenv.cfg
├── .python-version
├── README.md
├── main.py
├── pyproject.toml
└── uv.lock

```


#### pyproject.toml {#pyproject-dot-toml}

-   This file contains the metadata about the project in question, that can either be added manually by editing this file or by running certain commands. Sample file:

<!--listend-->

```text

  [project]
name = "hello-world"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
dependencies = []

```


### Adding dependencies to the project {#adding-dependencies-to-the-project}

```bash
uv add request #package versions can be specified
```


### Removing dependencies from the project {#removing-dependencies-from-the-project}

```bash
uv remove request
```


### Running a program and running a script {#running-a-program-and-running-a-script}

```bash
#program
uv add flask
uv run --flask run -p 3000
#script
uv run <python_file_name>
```


### Updating the environment {#updating-the-environment}

```bash
uv sync
```


### Note: UV does not activate virtual environment using these command. One needs to activate the virtual environment first before running scripts or programs. {#note-uv-does-not-activate-virtual-environment-using-these-command-dot-one-needs-to-activate-the-virtual-environment-first-before-running-scripts-or-programs-dot}


### Creating virtual environment using uv {#creating-virtual-environment-using-uv}

```bash
uv venv #creates .venv
uv venv <venv_name> #creates virtual environment named venv_name
```


## Integration with emacs {#integration-with-emacs}


### Install uv-mode: [link](https://github.com/z80dev/uv-mode) {#install-uv-mode-link}


### Instructions {#instructions}

-   UV Mode works automatically once installed. Simply open a Python file in a project that has a .venv directory, and UV Mode will activate the appropriate virtual environment.
