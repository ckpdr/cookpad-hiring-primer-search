# Technical exercise prerequisites

Follow this guide to make sure that you have all the prerequisites needed for the 
exercise. By the end of this guide, you will be able to:

- Create a local environment using [Pipenv](https://github.com/pypa/pipenv).
- Install some placeholder dependencies from that environment, using the Pipfile and required Python version.
- Build and run Docker containers with docker-compose

## Python Setup

### Pipenv installation

You can follow the instructions to install pipenv [here](https://github.com/pypa/pipenv#installation).

### Pipenv basic usage

Once Pipenv is installed, make sure you can run the following command that would install python 3.9 in a virtual environment: 

```bash
pipenv install
```

The above command should produce an output like:

```bash
$ pipenv install
Creating a virtualenv for this project...
Pipfile: /Users/user123/Documents/GitHub/ckpdr/cookpad-hiring-primer-search/Pipfile
Using /usr/local/bin/python3.9 (3.9.5) to create virtualenv...
⠙ Creating virtual environment...created virtual environment CPython3.9.5.final.0-64 in 734ms
  creator CPython3Posix(dest=/Users/user123/.local/share/virtualenvs/cookpad-hiring-primer-search--SzPdDog, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/Users/user123/Library/Application Support/virtualenv)
    added seed packages: pip==21.1.3, setuptools==57.0.0, wheel==0.36.2
  activators BashActivator,CShellActivator,FishActivator,PowerShellActivator,PythonActivator,XonshActivator

✔ Successfully created virtual environment! 
Virtualenv location: /Users/user123/.local/share/virtualenvs/cookpad-hiring-primer-search--SzPdDog
Installing dependencies from Pipfile.lock (4fa623)...
  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 5/5 — 00:00:02
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.

```

Once the dependencies have been installed in the local environment, confirm that:

```bash
$ pipenv run python --version
python 3.9.x
```

As an alternative, you can activate the environment. This way you won't have to type `pipenv run` before any command:

```bash
$ pipenv shell
(cookpad-hiring-primer-search) $ python --version
python 3.9.x
```

### Python troubleshooting

In case `pipenv install` command outputs:

```bash
$ pipenv install
Warning: Python 3.9 was not found on your system…
You can specify specific versions of Python with:
  $ pipenv --python path/to/python
```

We would recommend to use [Pyenv](https://github.com/pyenv/pyenv) to install and manage multiple python versions on your laptop. The installation instructions can be found [here](https://github.com/pyenv/pyenv#installation).

Once `pyenv` is installed, you would be able to install the python version required in the `Pipfile`:

```bash
$ pyenv install 3.9
$ pyenv local 3.9
```

Now `pipenv install` should produce the expected result.

## Docker Desktop setup

### Docker Desktop installation

You can follow the instructions to install Docker Desktop tools for:
 - Mac [here](https://docs.docker.com/docker-for-mac/install/)
 - Windows [here](https://docs.docker.com/docker-for-windows/install/)

Note: If you already have Docker Desktop installed, we use Compose File Version 3.3 in this exercise so we [require docker engine 17.06.0](https://docs.docker.com/compose/compose-file/compose-versioning/) or higher.

### Build and run Docker containers

Open a shell in the root of this repo and execute:

```bash
docker-compose up -d
```

This may take a few minutes the first time as Docker pulls layers locally, but these should be cached for next time.

Once successful you should see messages similar to the following:

```
Creating network "cookpad-hiring-primer-search_elk" with driver "bridge"
Creating cookpad-hiring-primer-search_elasticsearch_1 ... done
Creating cookpad-hiring-primer-search_kibana_1        ... done
```

Once complete, you should be able to access Kibana using the default username and password, `elastic /  changeme`, 
at http://localhost:15601 (with the ElasticSearch endpoints at http://localhost:19200).

Once complete, you can stop and remove the containers as follows:

```bash
docker-compose down -v
```

### Docker troubleshooting

- If you receive an error message similar to `Bind for 0.0.0.0:19200 failed: port is already allocated` then you may need
 to adjust the port for Elastic (ELASTIC_PORT) or Kibana (KIBANA_PORT) in the .env file and try again. You may need to repeat
 the config change in the exercise repo you receive.
