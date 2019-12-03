# Technical exercise prerequisites

Follow this guide to make sure that you have all the prerequisites needed for the 
exercise. By the end of this guide, you will be able to:

- Create a local environment using [Pipenv](https://github.com/pypa/pipenv).
- Install some placeholder dependencies from that environment, using the Pipfile and required Python version.
- Build and run Docker containers with docker-compose

## Instructions

### Pipenv installation

You can follow the instructions to install pipenv [here](https://github.com/pypa/pipenv#installation).

### Pipenv basic usage

Once Pipenv is installed, make sure you can run the following command that would install python 3.7 in a virtual environment: 

```bash
pipenv install
```

The above command should produce an output like:

```bash
$ pipenv install
Creating a virtualenv for this project…
Pipfile: /Users/user123/Documents/Code/interviews/dummy-python-project/Pipfile
Using /Users/user123/.pyenv/versions/3.7.2/bin/python3 (3.7.2) to create virtualenv…
⠧ Creating virtual environment...Already using interpreter /Users/user123/.pyenv/versions/3.7.2/bin/python3
Using base prefix '/Users/user123/.pyenv/versions/3.7.2'
New python executable in /Users/user123/.local/share/virtualenvs/dummy-python-project-c-zjErDL/bin/python3
Also creating executable in /Users/user123/.local/share/virtualenvs/dummy-python-project-c-zjErDL/bin/python
Installing setuptools, pip, wheel...
done.
Running virtualenv with interpreter /Users/user123/.pyenv/versions/3.7.2/bin/python3

✔ Successfully created virtual environment! 
Virtualenv location: /Users/user123/.local/share/virtualenvs/dummy-python-project-c-zjErDL
Installing dependencies from Pipfile.lock (a65489)…
  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 0/0 — 00:00:00
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
```

Once the dependencies have been installed in the locall environment, confirm that:

```bash
$ pipenv run python --version
python 3.7
```

As an alternative, you can activate the environment. This way you won't have to type `pipenv run` before any command:

```bash
$ pipenv shell
(python-exercise-primer) $ python --version
python 3.7
```

## Troubleshooting

In case `pipenv install` command outputs:

```bash
$ pipenv install
Warning: Python 3.7 was not found on your system…
You can specify specific versions of Python with:
  $ pipenv --python path/to/python
```

We would recommend to use [Pyenv](https://github.com/pyenv/pyenv) to install and manage multiple python versions in your laptop. The installation instructions can be found [here](https://github.com/pyenv/pyenv#installation).

Once `pyenv` is installed, you would be able to install the python version required in the `Pipfile`:

```bash
$ pyenv install 3.7
$ pyenv local 3.7
```

Now `pipenv install` should produce the expected result.

### Docker Desktop installation

You can follow the instructions to install Docker Desktop tools for:
 - Mac [here](https://docs.docker.com/docker-for-mac/install/)
 - Windows [here](https://docs.docker.com/docker-for-windows/install/)

