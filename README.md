# A Python packaging example

A very basic Python package skeleton that illustrates how to use `setuptools` and absolute imports to package a Python project that can be run as a command from a terminal.

It was a struggle for me to wrap my head around how to package a Python project, so I made this repo for my own notes, and to help others who are starting out and having the same struggles.

This README shows how to install and run the example, and provides some notes about how it works. The source code also has some explanatory comments (take a look at `pyproject.toml` in particular).

## How to install and run

1. Create a virtual environment and activate it (or use an existing environment):
	- `$ pip install virtualenv`
	- `$ python -m venv my_venv`
	- If using Linux: `$ source my_venv/bin/activate`
	- If using Windows: `> my_venv/Scripts/activate.ps1`
2. Once your virtual environment is activated, change to the project directory:
	- `(my_venv) $ cd pkg_example`
3. Then install with pip:
	- `(my_venv) $ pip install .`
4. Run the example (you don't need to be in the project directory to run this command - you can run it from any folder, provided the virtual environment is active):

	(my_venv) $ pkg_example
	Hello world!
	Did you know that 2 + 2 = 4?

## How does it work?

1. Once you `pip install` the package, you'll have a `pkg_example` binary in your PATH that you can run just like you run any other command from your terminal (eg `pip`, `cd`, `source`, ...)
3. When you run this command, Python will call the `main()` function inside the `main.py` file
	- This `main()` function is the "entry point"
	- You can specify the entry point function, and which module contains the function, in the `[project.scripts]` section of the `pyproject.toml` file
4. The entry point function is what executes the rest of the code in your Python package

## Package structure

	pkg_example
	├── pkg_example
	│   ├── __init__.py
	│   ├── main.py
	│   ├── my_adder.py
	│   └── my_subpackage
	│       ├── __init__.py
	│       └── hello_world.py
	├── pyproject.toml
	├── README.md
	└── setup.py

## Files

* `pkg_example` - The project folder that contains your Python package, the packaging files (`pyproject.toml` and `setup.py`), the README, and other project files separate from code (eg documentation, tests, `LICENSE`)
* `pkg_example/pkg_example` - The package containing the Python code
* `__init__.py` - A (often blank) file that tells Python that the containing folder is a Python package
* `main.py` - The module containing the main "entry point" function that will be called when you run the `pkg_example` comand in your the terminal
* `my_adder.py` - A module containing a simple function that takes two parameters and returns their sum
* `my_subpackage` - A subpackage containing additional functionality
* `hello_world.py` - A module containing the function that `main()` in `main.py` calls when you run the `pkg_example` command
* `pyproject.toml` - The configuration file that tells `setuptools` how to configure and build your Python package
* `setup.py` - The module that initializes `setuptools` when you `pip install` the package

## Resources

Some Python packaging resources that may be helpful are:

* https://py-pkgs.org
* https://setuptools.pypa.io/en/latest/userguide/quickstart.html 
