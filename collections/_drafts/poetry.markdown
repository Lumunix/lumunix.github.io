---
layout: Post
title: Being a Tmate - Sharing a Terminal Session
description: How to share your terminal session with mac users.
author: lumunix
date: 2022-05-26
thumbnail: /assets/img/codesections.png
image: /assets/img/codesections.png
header: /assets/img/banner.png
tags: [Terminal,Collaboration,Tools, Pair Programming]
comments: false
---

So you start on a python project, you open your IDE and say your starting from a existing framework or generated template, you are probably familiar with the following pip install command:


```
pip install -r requirements.txt
```
When you are setting up a project you have to create a virtual environment, installing dependencies, running any setup scripts for the project as well as dealing with the files `setup.py`, `requirements.txt`, `setup.cfg`, `MANIFEST.in` and `Pipfile`that are required for setting up the project and configuring your development setup. The python project [Poetry](https://python-poetry.org) aims to simply the setup of a project with a single .toml file `pyproject.toml`. Were going to dive into an introduction into installing and utilizing poetry in a python project. This is only an introduction to Poetry, as always please [Read the docs](https://python-poetry.org/docs/) for the latest information.


{:toc}
## What is Poetry ?
> Poetry is a tool for dependency management and packaging in Python. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you. Poetry offers a lockfile to ensure repeatable installs, and can build your project for distribution. 

### Use Cases
- Handle packaging and versioning
- Manage virtual environments creation
- Install and manage dependencies and versions for your project
- Centralize project configuration and management
- Publishing python packages


## Prerequisites
This guide assumes you have installed and configured [Python](https://www.python.org/downloads/) on your machine.


## Installing Poetry
Installing poetry on your system can be done with a simple command in Terminal or Powershell, depending on your system.

### MacOS
Open a terminal window and execute the following command:
```
curl -sSL https://install.python-poetry.org | python3 -
```
### Windows
Open a powershell window and execute the following command:
```
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

You can check that poetry is installed correctly afterwards by checking the version:
```
poetry --version
Poetry (version 1.4.2)
```

## Initialize Poetry in a Python Project
Poetry can be used to bootstrap a new python projects or added to an already existing project. In this example were going to create a new project to gain a better understanding of how poetry functions. 
### Creating a New Python Project Using Poetry
Creating a new python project that is already configured to use poetry is straightforward and can be done with the 'new' command in poetry. 

```
poetry new pythonproject
```

On the creation of a new python project using poetry you should see a file tree structure similar to the following one.

```
├── pyproject.toml
├── pythonproject
│   └── __init__.py
├── README.md
└── tests
    └── __init__.py
```
Opening the *pyproject.toml* file, we can see this contains all the information to manage our python project. There are 4 distinct sections in the default toml file.

- [tool.poetry]: This section defines project metadata, this includes the name of the package, description, license information, authors and the current version number.
- [tool.poetry.dependencies]: This section defines all the dependencies for our python project.

```
[tool.poetry]
name = "pythonproject"
version = "0.1.0"
description = ""
authors = ["Lumunix <lumunix@icloud.com>"]
readme = "README.md"

[tool.poetry.dependencies]
python = "^3.11"

[tool.poetry.dev-dependencies]
python = "^7.4"

[build-system]
requires = ["poetry-core"]
build-backend = "poetry.core.masonry.api"
```

### Adding Poetry to an Existing Python Project
If you want to add poetry to an existing python project, or don't want poetry to initialize a project for you, you can use the 'init' command that will open an interactive shell that will allow you to configure your project to use poetry.

```
# Run interactive shell to configure a project ot use poetry.
poetry init
```
### Opening an Existing Python Project That Uses Poetry
Say you have taken a new job and a (awesome) python developer has already added poetry to a project and you are setting up the project for the first time. Setting up a development environment can be done with the 'install' command. This command creates a virtual environment and installs all the dependencies for the project, its like magic!

Please note that poetry by default does not create a virtual environment inside the project directory, if you want the virtual environment to be under the project directory please set the virtualenvs to be inside the project. This is useful if you ever delete the root folder the virtual environment is deleted as well rather than being stored in a separate directory.

```
# Setting virtual environment to be inside the project directory
poetry config --local virtualenvs.in-project true
# Install dependencies and initialize the project
poetry install
```



## Adding/Removing Dependencies

Lets say you are creating a new python project and you want to add python [requests](https://pypi.org/project/requests/) dependency to perform api calls or web interactions. Adding the dependency to the project can be done with an add command. If you want to add a development only dependency you can pass the -D argument, in this example say we want to add the [pytest](https://docs.pytest.org/en/7.4.x/) dependency to write tests against the project.

```
# Add the requests dependency
poetry add requests

# Add the pytest development dependency 
poetry add -D pytest
```
If you need to remove a dependency, the remove command can be used as the inverse to the add command.
```
# Remove the requests dependency
poetry remove requests

# Remove the pytest development dependency 
poetry remove -D pytest
```

## Viewing and Updating Dependencies
Updating dependencies in projects can be tedious, poetry tries to make this simpler with the *show* and *update* command. Lets say your evaluating dependencies to update in your project, by utilizing the show command we can see a dependency tree for our project. This way its easy to see all the direct project dependencies as well as transient dependencies. 


```python
# Show the dependency Tree 
poetry show --tree
allure-pytest-bdd 2.13.1 Allure pytest-bdd integration
├── allure-python-commons 2.13.1
│   ├── attrs >=16.0.0 
│   └── pluggy >=0.4.0 
├── pytest >=4.5.0
│   ├── attrs >=19.2.0 
│   ├── colorama * 
│   ├── exceptiongroup >=1.0.0rc8 
│   ├── iniconfig * 
│   ├── packaging * 
│   ├── pluggy >=0.12,<2.0 
│   └── tomli >=1.0.0 
└── pytest-bdd >=3.0.0

```

Utilizing the *show* command with the --latest flag we can get an entire list of dependencies with their latest version available. 

```python
# Show the dependency list with latest versions of each dependency
poetry show --latest
allure-pytest-bdd     2.13.1    2.13.2   Allure pytest-bdd integration
allure-python-commons 2.13.1    2.13.2   Common module for integrate allure with python-based frameworks
async-generator       1.10      1.10     Async generators and context managers for Python 3.5+
attrs                 22.2.0    23.1.0   Classes Without Boilerplate
certifi               2022.12.7 2023.5.7 Python package for providing Mozilla's CA Bundle.
charset-normalizer    3.1.0     3.2.0    The Real First Universal Charset Detector. Open, modern and actively maintained alternative to Chardet.
exceptiongroup        1.1.1     1.1.2    Backport of PEP 654 (exception groups)
h11                   0.14.0    0.14.0   A pure-Python, bring-your-own-I/O implementation of HTTP/1.1
idna                  3.4       3.4      Internationalized Domain Names in Applications (IDNA)
iniconfig             2.0.0     2.0.0    brain-dead simple config-ini parsing
mako                  1.2.4     1.2.4    A super-fast templating language that borrows the best ideas from the existing templating languages.
markupsafe            2.1.2     2.1.3    Safely add untrusted strings to HTML/XML markup.
outcome               1.2.0     1.2.0    Capture the outcome of Python function calls.
packaging             23.0      23.1     Core utilities for Python packages


```

Updating packages is straightforward with the *update* command. The update command will update all dependencies in the project. If you prefer you can use the update command with a single dependency to only update that particular dependency. 

```python
# Update all dependencies
poetry update
# Update the requests dependency
poetry update requests
```

## Building a Python Project Using Poetry
Building a project using poetry is also straightforward with the *build* command, note that you can also specify the type of output, either a whl or sdist file.

```python
poetry build
# Build a whl file
poetry build -F wheel
# or sdist file
poetry build -F wheel 
```


## Publishing a Python Package Using Poetry
Poetry can be used to configure where to publish artifacts for your python package. Lets say we need to publish our python package to a private package repository. We can configure this using the poetry *config* command. 

In this example the repo name is "companyrepo" with the url "https://company.repository".  

```python
# poetry config repositories.<reponamehere> <url-for-repo-here>
poetry config repositories.companyrepo https://company.repository
```

If we don't feel like writing our username and password each time we publish, using the *config* command we can configure the authentication.  
```python
# Save credentials as part of config
poetry config http-basic.companyrepo username password
```
Executing the *publish* command with the argument of our private repository name will publish the package. 

```python
# Publishing package to companyrepo
poetry publish -r companyrepo
```

Thank you for the read if you made it this far! If you or another developer found this tutorial helpful, please leave a comment below. 



