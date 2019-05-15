# Chrome Selenium

## Software Installed

* Google Chrome Browser Version 74
* Selenium Version 3.141.59
* Python 2.7

## How To Use

### Testing Locally

If you wish to use the container to run tests from your local machine, first clone this repository to your machine:

```console
git clone git@git@github.com:ndlib/docker_python_selenium.git
```

Next, navigate in a terminal session to the cloned directory:

```console
cd /path/to/cloned/repository
```

The container will need to be built once from the provided Dockerfile. To do this, run the following after navigating to the repository (note, you may use any name for the container on your machine):

```console
docker build --rm -f "SeleniumChrome/Dockerfile" -t nameofcontainer:latest SeleniumChrome
```

Once the container is build, you can enter it in an interactive manner, mount a local directory into the container, and run your tests using Python inside the container.

As an example:

1. I have tests created in my /tests/python directory.
1. I want the tests in this directory to be available in the /etc/selenium directory within the container.
1. I do not wish to have these tests as a permanent part of the container, as I will be iterating on them in development.

Run the following command to enter the container in an interactive manner:

```console
docker run -v /full/path/to/tests/python:/etc/selenium -it nameofcontainer /bin/sh
```

If you need to pass in environment variables to the container, this can be done with the `-e` flag within Docker, as follows:

```console
docker run -v /Users/ialford/git/ezproxy_config/spec/selenium:/etc/selenium -ite EnvironmentVar1='value-of-environment-variable' -e EnvironmentVar2='value-of-other-environment-variable' seleniumchrome_nd /bin/sh
```

Once in the container, you may need to make your python scripts executable. You may do this by running the following (assuming that you have placed your scripts in the /etc/selenium directory):

```console
chmod -R u+x /etc/selenium
```

Lastly, execute your desired test script as follows, specifiying the specific script you wish to run:

```console
python /etc/selenium/path/to/test.py
```
