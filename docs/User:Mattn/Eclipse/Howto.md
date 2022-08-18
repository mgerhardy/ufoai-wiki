## General

This howto is about the installation and the setup of [Eclipse
Wascana](http://code.google.com/a/eclipselabs.org/p/wascana/) on a
Windows platform to compile and develop for UFO: Alien Invasion

## Step 1: Getting the required software

- Download
  [Wascana](http://code.google.com/a/eclipselabs.org/p/wascana/downloads/list)
- Download [Git](http://code.google.com/p/msysgit/downloads/list) (Use
  the full installer of the official Git version)
- Download [MinGW Extensions](http://localhost) to be able to compile
  and link UFO: Alien Invasion <font color="red">This is still missing,
  but I'm working on it</font>

## Step 2: Install the downloaded software

- Wascana must be installed in . If you change this directory, you would
  have to edit all the pkg-config files that you have to install in the
  next step.
- After Eclipse Wascana is installed you can install the MinGW extension
  package.
- Install Git

## Step 3: Clone the git repository

See [Getting the source](Getting_the_source "wikilink")

## Step 4: Environment variables

![](Set-cc-env-var.png "Set-cc-env-var.png") Change your PATH to also
include the and directories. Add a new variable named CC and set it to
gcc.

## Step 5: Start Wascana

![](Eclipse-wascana-include-dirs.png "Eclipse-wascana-include-dirs.png")
![](Eclipse-import-existing-project.png "Eclipse-import-existing-project.png")
![](Eclipse-import-existing-project-step2.png "Eclipse-import-existing-project-step2.png")
Start Eclipse Wascana and import the cloned repository. Go to
File-\>Import-\>Existing Project, select the directory and import the
shown project.

You are now able to build and link UFO: Alien Invasion

[Category:Coding](Category:Coding "wikilink")
[Category:Contribute](Category:Contribute "wikilink")