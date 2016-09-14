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
In the realm of continuous integration there is usually a source code repository.
The source code repository is usually technologies like git, svn, cvs or other version and source controlling software.
The idea of the source code repository is to allow for efficient ways to handle code changes and to manage multiple developers working on the same code.

Lastly, there is a server, running software similar to Jenkins CI or Travis CI which can potentially handle many tasks.
At a high level, it is usually used to run a build or test step in, say, a build.gradle, project.json, Makefile or various other build tools.
To enhance tools like Jenkins, there are binary and other code quality scans like SonarQube and others which attempt to find issues outside of the space of unit and mock tests.
Other such triggers, like diff checking, can be used to trigger code reviews for massive revisions of source code.

Generally, the final stage of Continuous Integration is to notify the developers, or other interested parties, the results of these various tests and builds.
In a full CICD build pipeline, generally there is the process of uploading so called artifacts to a artifact or binary repository.
These binary repositories are more in the realm of continuous delivery.

![An example Continuous Integration Workflow](media/ci.png)

Continuous delivery also has it's share of tools and structure.
One of the first requirements of continuous delivery is having some form of binary repository.
For java based projects, there are things like nexus.
Other languages, like python, have their own packaging sites;
python for instance has PyPI.

In order to deploy these binaries, many tools make use of remote shell protocols.
Remote shell protocols give tools access to execute the needed steps to get software deployed.
Generally these tools run through scripts which make the machine require the needed binaries and create the needed configurations.
The remote shells are no different than conventional user-controlled shells.

There are various tools and servers that do this; a few examples are Ansible, uDeploy and Puppet.
Ansible uses remote shell protocols, such as secure shell (ssh), to execute a set of instructions written in yaml, generally with the intent of installing some type of software.
uDeploy is similar in how it causes change on target machines, using secure shell; however uDeploy generally requires the target machines to be running some kind of daemon.

Many POSIX-like systems make use of package management to deliver software.
Packages, like .deb's and .rpm's, are a collection of installation shell scripts, including pre-installation and post-installation, and a binary or source code.
Package managers, as their name implies, also manages these installed binaries, scripts and configurations.
Part of their management requires tracking file locations. This allows for rolling back, upgrading or removal of installed files.

Deployment strategy can be different depending on the available infrastructure.
In an environment with fixed inventory, it might not be ideal to do things like \`make install\` which are hard to reverse.
However in an environment where machines can be spun up at whim, or even automatically, it wouldn't matter as much; in such cases one would simply destroy and create a new machine for every deployment.
In a fixed architecture, it might be ideal to stick to package management solutions for delivering binaries.
It might not matter if it is dynamic as the cleanliness of the system.

![Example Continuous Deployment setup[^cd]](media/cd.png)

[^cd]: more akin to a uDeploy setup, a master server orchestrates actions to be take against numerous machines; generally the machines fetch the binaries they need to install from an artifact repository. Master can be triggered to action by the CI system as well.
