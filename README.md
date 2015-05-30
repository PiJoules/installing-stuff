# Installing Stuff
Guide for installing various things on a new linux such as java, pip, etc. via `apt-get`.

## Links to other stuff
- [Markdown](https://help.github.com/articles/markdown-basics/)
- [Setting up a Flask Application on Apache](https://github.com/PiJoules/FlaskApache)

## Java
This is for installing the default JRE/JDK.

1) Update the package index.
```sh
$ sudo apt-get update
```

2) Check if Java is already installed. No need to follow the rest of the steps if it is.
```sh
$ java -version
```

3) If Java hasn't been installed yet, install the Java Runtime Environment.
```sh
$ sudo apt-get install default-jre
```

4) Install the Java Development Kit. This is usually need to compile some Java applications (like Ant, Maven, Eclipse, etc.).
```sh
$ sudo apt-get install default-jdk
```

At this point, you should have Java installed. You can check the version used by running:
```sh
$ java -version
```

## Pip
1) Install `setuptools` using `curl`.
```sh
$ curl https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py | sudo python -
```

2) Install `pip`.
```sh
$ curl https://bootstrap.pypa.io/get-pip.py | sudo python -
```

3) Check if `pip` is installed by running
```sh
$ pip -version
pip 7.0.1 from /usr/local/lib/python2.7/dist-packages (python 2.7)
```

4) The setuptools zip file may be in the current directory. If pip is successfully installed, this can be deleted.
```sh
$ rm setuptools-16.0.zip
```

## Git
Various things to setup with git

### Installing Git
```sh
$ sudo apt-get install git
...
$ git --version # just to check if installed successfully
git version 1.9.1
```

### [Password Caching](https://help.github.com/articles/caching-your-github-password-in-git/)
This will turn on the credential helper so that Git will save your password in memory for some time. This requires Git **1.7.10** or newer. By default, Git will cache your password for 15 minutes.

1) Set git to use the credential memory cache. (Default is 15 min.)
```sh
$ git config --global credential.helper cache
```

2) To change the default password cache timeout **(in seconds)**, enter the following:
```sh
$ git config --global credential.helper 'cache --timeout=[# of seconds]'
```

After pushing (and entering your password one more time), you then should be able to push to remote without having to enter a username or password again until the timeout is reached.