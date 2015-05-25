# Installing Stuff
Guide for installing various things on a new linux such as java, pip, etc. via `apt-get`.

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
$ sudo apt-get install default-jre
```

At this point, you should have Java installed. You can check the version used by running:
```sh
$ java -version
```