---
# you can add comments describing
# what the section is for
# in between the --- lines.
---

2. Background
=============

CICD is the process of accelerating the building, testing and installation of applications to end servers .
In a world where web technology moves fast and new features are ideal, it's critical to go to market fast.
To do this there are two major architectures that are used.
CI, continuous integration is concerned with the development process.
In the realm of continuous integration there is usually the concept of a source code repository.
The source code repository is usually something like a remote git, svn, cvs or other version controlled technology.
The idea of the source code repository is to allow for efficient ways to handle code changes and to manage multiple developers working on the same code.

Lastly, there is a server, running software similar to Jenkins CI or Travis CI which can potentially handle many tasks.
At a high level, it is usually used to run a build or test step in, say, a build.gradle, project.json, Makefile or various other build tools.
To enhance tools like Jenkins, there are binary and other code quality scans like SonarQube and others which attempt to find issues outside of the space of unit and mock tests.
Other such triggers, like diff checking, can be used to trigger code reviews for massive revisions of source code.

Generally, the final stage of Continuous Integration is to notify the developers, or other interested parties, the results of these various tests and builds.
In a full CICD build pipeline, generally there is the process of uploading so called artifacts to a artifact or binary repository.
These binary repositories are more in the realm of continuous delivery.

Continuous delivery also has it's share of tools and structure.
One of the first requirements of continuous delivery is having some form of binary repository.
For java based projects, there are things like nexus.
Other languages, like python, have their own packaging sites;
python for instance has PyPI.

In order to deploy these binaries, many tools make use of remote shell protocols.
Remote shell protocols give tools access to execute the needed steps to get software deployed.
Generally these tools run through scripts which make the machine require the needed binaries and create the needed configurations.

There are various tools and servers that do this; a few examples are Ansible, uDeploy and Puppet.
Ansible uses remote shell protocols, such as secure shell, to execute a set of instructions written in yaml, generally with the intent of installing some type of software.
uDeploy is similar in how it causes change on target machines, however it also includes various other features and also a daemon to be running on the target machine.

Many POSIX-like systems make use of package management to deliver software.
Packages, like .deb's and .rpm's, are a collection of installation shell scripts, including pre-installation and post-installation, and a binary or source code.
Package managers also manage what is installed by convention making it easy to keep track of what is installed and where it is installed.
Because of this, rolling back, upgrading or removal is simplified.
