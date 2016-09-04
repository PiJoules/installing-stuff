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
$ curl https://bootstrap.pypa.io/ez_setup.py | sudo python -
```

2) Install `pip`.
```sh
$ curl https://bootstrap.pypa.io/get-pip.py | sudo python -
```

3) Check if `pip` is installed by running
```sh
$ pip --version
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

### [Removeing multiple files from a git repo](http://stackoverflow.com/questions/492558/removing-multiple-files-from-a-git-repo-that-have-already-been-deleted-from-disk)
If you ever end up with something like this
```sh
# Changes not staged for commit:
#   (use "git add/rm <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	deleted:    content/posts/firstpost.md
#	deleted:    content/posts/secondpost.md
#	deleted:    static/css/blog.min.css
#	deleted:    static/css/hilite.css
#	deleted:    static/js/bootstrap.min.js
#	deleted:    static/js/jquery-1.11.0.min.js
```
and want to remove all these files that were already removed from the disk without typing `git rm file1 file2 file3 file4`, use this to delete all files that were deleted, but not staged for commit:
```sh
$ git rm $(git ls-files --deleted)  
```

## [MongoDB](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-ubuntu/)
These steps are for installing MongoDB on Ubuntu 12.04+.

### Installing MongoDB
1) Import the public key used by the package management system.
```sh
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
```

2) Create a list file for MongoDB.
```sh
$ echo "deb http://repo.mongodb.org/apt/ubuntu "$(lsb_release -sc)"/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
```

3) Reload local package database.
```sh
$ sudo apt-get update
```

4) Install the latest version of MongoDB.
```sh
$ sudo apt-get install -y mongodb-org
```
OR install a specific release of MongoDB (say 3.0.4)
```sh
$ sudo apt-get install -y mongodb-org=3.0.4 mongodb-org-server=3.0.4 mongodb-org-shell=3.0.4 mongodb-org-mongos=3.0.4 mongodb-org-tools=3.0.4
```

5) `(Optional)` If you want to prevent from updating to the next available version of MongoDB every time you run `aot-get update`, you can pin the currently installed version and ignore any new package updates.
```sh
$ echo "mongodb-org hold" | sudo dpkg --set-selections
$ echo "mongodb-org-server hold" | sudo dpkg --set-selections
$ echo "mongodb-org-shell hold" | sudo dpkg --set-selections
$ echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
$ echo "mongodb-org-tools hold" | sudo dpkg --set-selections
```

### Running MongoDB
1) Starting the MongoDB server
```sh
$ sudo service mongod start
```

2) Stopping the MongoDB server
```sh
$ sudo service mongod stop
```

3) Restarting the MongoDB server
```sh
$ sudo service mongod restart
```

4) Accessing the MongoDB shell
```sh
$ mongo
```
