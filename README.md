# JDart-Viz
JDart-Viz is a visualization tool which lively illustrates the constraints trees generated by [JDart](https://github.com/psycopaths/jdart), a dynamic symbolic analysis tool for Java. JDart-Viz can significantly relieve the pain when analyzing the result trees JDart produces for us. The [demo page](http://chaofz.me/jdart-viz) provides a presentation to help getting the gist of this tool.

This project is a participation project of [Google Summer of Code 2016 (GSoc 2016)](https://developers.google.com/open-source/gsoc/) under the team [Java Pathfinder](http://babelfish.arc.nasa.gov/trac/jpf). Here is the [description](http://chaofz.me/jdart-viz/description) of the project.

### Installation

#### 1. Install JDart

Since JDart-Viz is a visualization tool for JDart, we need to install JDart first. Thanks to [Marko Dimjašević](https://dimjasevic.net/marko/) who has set up a Vagrant environment for JDart so that JDart can be installed by one command.

Checkout out [JDart](https://github.com/chaofengzhou/jdart) repository (currently the version I have been working on):

```sh
$ git clone https://github.com/ChaofengZhou/jdart.git
```

Make sure you have installed [Vagrant](https://www.vagrantup.com/), a virtual development environment tool. Additionally, you need either VirtualBox or libvirt.

If Vagrant is ready, change to jdart directory and run:

```sh
$ vagrant up
```

The [JDart repository](https://github.com/psycopaths/jdart) provides thorough installation instructions. You can also check them out if you want to install it without a virtual machine.

#### Add jpf on PATH

JDart-Viz requires jpf, which JDart is based on and you have just installed, on PATH. Append `export PATH=$PATH:/path/to/jpf-core/bin` to the bash profile file depending on your operating system.

#### Install JDart-Viz

First, install Node.js on your machine. If you have already installed node (with npm), you can skip to the next step. There are various ways to install node. Details can be found on [nodejs.org](https://nodejs.org/en/).

If you are using Ubuntu or Debian, node on these OS's is named as nodejs. So, please link `nodejs` to `node` by 

```sh
sudo ln -s $(which nodejs) /usr/bin/node
```

Second, install Gulp:

```sh
$ npm install --global gulp-cli
```

Build and link the project:

```sh
$ npm install
$ gulp build
$ npm link
```

JDart-Viz has been published as an NPM package. If you don't want to build it, simply run:

```sh
$ npm install --global jdart-viz
```

### Workflow & Usages

#### Workflow

JDart-Viz depends on the JSON-formatted file JDart generates. Therefore, the first thing we should do is to run JDart upon a method. To make that happen, we need to configure a .jpf file which contains the instructions how we dictate jpf to run.

The following two config options dictate jpf to output JSON under the current directory. Make sure they are appended in the jpf file:

```sh
jdart.tree.json.print=true
jdart.tree.json.dir=.
```

Then, we can run JDart-Viz towards the jpf config files by executing `jdart-viz <target.jpf>` which wraps the instruction `jpf <target.jpf>`.

After jpf terminates, JDart-Viz takes the output JSON file as input and visualize the result graphically.

#### Usages

Initiate the server first:

```sh
$ jdart-viz serve
```

Now we can run `jdart-viz` upon JPF config files. Navigate to the directory containing jpf config files, and run

```sh
$ jdart-viz <target.jpf>
```

A browser will pop up for you to enjoy the power of this visualization project.

<!-- ### Installation

#### 1. Install JDart

JDart-Viz is a supplimental tool for JDart so JDart should be installed.

Thanks to [Marko Dimjašević](https://dimjasevic.net/marko/) who has set up a Vagrant environment for JDart so that JDart can be installed by one command.

Checkout out JDart repository (currently the version I have been working on):

```sh
$ git clone https://github.com/ChaofengZhou/jdart.git
```

Make sure you have installed [Vagrant](https://www.vagrantup.com/), a virtual development environment tool. Additionally, you need either VirtualBox or libvirt.

If Vagrant is ready, change to jdart directory and run:

```sh
$ vagrant up
```

The [JDart](https://github.com/psycopaths/jdart) repository provides thorough installation instructions. You can also check them out if you want to install it without a virtual machine.

JDart-Viz requires jpf, which JDart is based on and you have just installed, on PATH. Append export `PATH=$PATH:/path/to/jpf-core/bin` to the bash profile file depending on your operating system.

#### 2. Install Node.js & Gulp

If you have already installed node (with npm), you can skip to the next step. There are various ways to install node. Details can be found on [nodejs.org](https://nodejs.org/en/).

Install Gulp

```sh
$ npm install --global gulp-cli
```

#### 3. Build and link the project

Change to the project directory and run

```sh
$ npm install
$ gulp build
$ npm link
```


### NPM package

JDart-Viz has been published as an NPM package. If you don't want to build the project, simply run

```sh
$ npm install --global jdart-viz
```


### Usages

Now you can run `jdart-viz` upon JPF config files as you run `jpf example.jpf` previously.

Initiate the server first

```sh
$ jdart-viz serve
```

then, navigate to the directory containing jpf config files, and run

```sh
$ jdart-viz example.jpf
```

A browser will pop up for you to enjoy the power of this visualization project. -->

### Development

If you want to develop more features for it, you can enter the dev mode by

```sh
$ gulp dev
```
