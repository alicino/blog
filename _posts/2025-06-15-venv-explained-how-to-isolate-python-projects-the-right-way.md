---
layout: single
title: "venv Explained: How to Isolate Python Projects the Right Way"
tags:
  - python
  - venv
  - intermediate
  - project
  - virtualenv
  - pip
  - environment
category:
  - python
  - environment
---

**venv** is a Python module used to create virtual environments. It’s useful when working on a project that requires specific dependencies or versions that differ from your global Python installation.

{% include figure image_path="/assets/images/2025-06-15-venv-explained-how-to-isolate-python-projects-the-right-way.png" alt="Python venv post Banner" class="align-center" width="450" %}

---

**Important**
This is a small part of coding and best practices in Python using virtual environments. I will address other points such as `pyenv` and `uv` in the future. For now, we can describe `venv` in more detail.

### How to create the virtual environment

Navigate to your project directory and run:

```bash
python -m venv .venv
```

A folder inside your project will be created with all dependencies you install there. It's possible to see the .venv folder created.

`.venv`  is just a common convention—you can name it whatever you like. However, best practices recommend using clear and standard names like .venv or venv for consistency

After that, you need to activate the virtual environment by typing the appropriate command for your Operating System:

| Operating System | Kind of Shell | Command |
| ---------------- | ------------- | ------- |
| Linux or Mac     | bash or zsh   | `$ source <venv>/bin/activate` |
| Windows          | cmd           | `C:\> <venv>\Scripts\activate.bat` |
| Windows          | PowerShell    | `C:\> <venv>\Scripts\Activate.ps1` |

Inside the `<venv>` directory, you’ll typically find a `bin` (on Unix) or `Scripts` (on Windows) folder, which contains the activation script.

To deactivate the environment, simply run `deactivate` in your terminal. No matter the OS.

### Installing packages

To install any package, the `venv` must be active. Then use the usual `pip` command, such as: 

```bash
pip install flask
```
To install a specific version, type:

```bash
pip install flask==2.3.3
```

### Checking all Packages installed

To check all package you have installed, type:
```bash
pip list
```

You should see an output like this:

```text
Package      Version
------------ -------
blinker      1.9.0
click        8.2.1
Flask        2.3.3
itsdangerous 2.2.0
Jinja2       3.1.6
MarkupSafe   3.0.2
pip          22.0.2
setuptools   59.6.0
Werkzeug     3.1.3
```

### More pip commands

To inspect a specific package and see its dependencies, use:

```bash
pip show flask
```

The output includes information like:

```
Requires: Werkzeug, Jinja2, MarkupSafe, ItsDangerous, Click
```

---
### Official Documentation

For more information, refer to the official Python documentation on [venv - Creation of virtual environments](https://docs.python.org/3/library/venv.html)

---

Let me know if you have any questions or need help setting up a venv for your projects!

