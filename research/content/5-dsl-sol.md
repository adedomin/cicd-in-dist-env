---
# Finish this by next meet
# bullets to paragraphs
# no two column
---

5. Limitation of Current Domain Specific Languages and Tools
============================================================

Below will be the explanation of a new DSL that I will develop that will attempt to solve shortfalls in other tools. 
Ideally, to also merge them into a universal testing, packaging and deployment framework.
The goals of the language are to solve the following shortfalls: 

5.1. Irreversibility
---------------------

As Stated earlier, many deployment tools make large number of untracked changes to the file system.
Such changes as creating directories, inserting configurations, binaries, scripts and other such files.
Other changes, like new users, added and enabled services, etc... to configurations are also untracked.

What is proposed is a simple key-value like database which can contain package name as keys and a value which is a document of changes -(more detail)-.

### 5.1.1. Detractions

The problem is, many CICD, or "DevOps", manuals expect you to do A-B deployments to prevent reversibility issue -(link to red hat customer portal)-.
This way, when issues arises, the DevOps engineer can simply destroy the new machine and go back to the old one.
Vise versa if the new machine is successful, the old one is destroyed.
To take it to an extreme, using docker and docker container OSes like CoreOS and Red Hat Atomic Linux, The whole operating system is to be considered immutable and any updates should destroy the previous state of the machine.

5.2. Build and Testing Tool Dependencies
----------------------------------------

Currently as it stands, most centralized CI systems depend on the infrastructure or operations team to manage needed build tool, and other testing, tools which can hinder the progress of developers to do their work;
ideally developers will be able to dictate their requirements and have them be met automatically, which is currently an issue with all the major CI build systems. 

One of the biggest problems in the CI space is dealing with the demands of developers and the tools they need.
Jenkins for instance is very difficult to work with when developers try to use tools that aren't available on the jenkins build server or servers.
As a result, self hosted CI tools like Jenkins depend on a very rich set of plugins that try to solve these "dependency hell" problems.

Certain build tools like Apache Maven and Gradle use the concept of "wrappers" which are usually shell scripts that "resolve" the build tool binary of the specified version.
However most depend on a binary file to accomplish this (describe issues with this?).
One of the issues with this is that, at a later date, if there are issues with the version being used or it is no longer available, many projects would need to be manually updated to use new versions of the build tool.
Binaries also pollute the source tree since they can not be differenced as easily as plain text documents, making it hard to track changes on the binary;
this can also cause issues with the size of the repo.
This also leads to having multiple copies of the same tool everywhere, with slightly different versions.
If for any reason these tools have bugs or worse, some kind of vulnerability, repositories would have to be assessed for this "broken" version.

### 5.2.1. Provided Services

For testing, it may be ideal to have services such as databases.
Currently, it's the same problem with build tools; either the server is provided, externally or locally.
It would be ideal to handle this problem in the language as well.

5.3. Options in Deployments
---------------------------

Currently, tools depend on remote shell protocols, as described earlier;
however, shell protocol security can make it costly to open connections and to send data to them.
For security reasons, concepts like asynchronous callbacks, can be difficult to achieve via shell protocols;
unless of course the server can ssh into the deployment server (I have never seen this in practice).

Ideally, for updating, there should be optional, web centric way of pulling changes.
Currently ansible is deployed manually, over shell.
After the initial deployment, there could be a script which would allow for "pulling" updates over the network.
To make ansible more as an automated service, projects like loopabull can add automation to the whole process.

5.4. "Artifacting"
------------------

The concept of artifacting is separating out the various components of an application into these versioned components.
Currently only uDeploy, as far as I know, offers such a construct.

The advantage of this is deployments are broken into logical pieces.
The Other advantage is the pieces are versioned as well;
This gives a user the ability to fine tune the product to find the best composition of versioned artifacts.

5.5. Order of execution
------------------------

Tools like ansible and puppet depend on tasks executing in a particular order. 
To attempt to add ordering, they add concepts like listeners and handlers.
However, it can be confusing at time and add unneeded complexity for simple tasks.

Ideally one would be able to use monadic constructs to add ordering, but to functionally encapsulate the side effect laden issues of deployment.
This could also help solve the irreversibly problem.

DSL should feature:

  * Multi-paradigm for describing deployments
    * graphs (Metamodeling - or Model driven)
      * Ideally with a drawing tool.
      * Alternatively, users could make graphs using the DOT language, or another simplier graph language.
    * sequential steps (yaml|toml|json|etc)
      * similar to ansible, puppet and many others.
  * Dependency management for playbooks & components
    * think npm, pip, etc.
    * requires playbooks and components have a package file that describes what they provide.
    * TravisCI leverages weaknesses in this problem to push it's nonfree software as a service platform.
  * Integration of all the key steps in a integration and deployment pipeline
    * Integration (testing) (see figure 3, shows domain problem at a high level)
    * Packaging (artifacting)
      * leverage language specific packaging?
    * Deployment
      * symlink management (like GNU Stow)
    * Configuration Management (see figure 4, shows proposed to manage configurations)
  * "Agentless" service
    * Utilize builtins only
      * standard POSIX utilities
    * Scripting languages
      * common languages like python 2
      * bash
    * no daemons/services
      * other than sshd or other remote shell service
      * pretty much ubiquitous

