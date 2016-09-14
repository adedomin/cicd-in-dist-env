---
# Finish this by next meet
# bullets to paragraphs
# no two column
---

5. Domain Specific Language for Integration, Packaging and Deployment
=====================================================================

Below will be the explanation of a new DSL that I will develop that will attempt to solve shortfalls in other tools. 
Ideally, to also merge them into a universal testing, packaging and deployment framework.
The goals of the language are to solve the following shortfalls: 

  * Irreversibility of many configuration management tools (ansible, puppet).
    * Many of the tools in use make untracked, and ultimately, difficult to revert, changes to the filesystem.
    * Tools should track needed changes to the filesystem so that they can be removed and cleaned up or possibly updated later.
    * Many CICD ("DevOps") manuals expect you to do A-B deployments to prevent reversibility issue (link to red hat customer portal).
      * A and B as in, when a new deployment needs to occur, build a new machine (say b) to deploy to and if it breaks, bring back the old machine (a in this example).
      * Some systems, for example CoreOS and Red Hat Atomic, take it to the extreme by having the OS be an immutable source tree which is entirely.
  * Resolving build tool, and other environment specific dependencies (jenkins)
    * There a various tools for languages like java: gradle, maven, ant, etc.
    * These tools may not be installed on the CI server.
    * To work around this, gradle and maven offer "wrapper" scripts.
      * This requires your project to ship with a gradle or maven jar files, java binaries.
    * In C/C++, people could be using GNU Autoconf, CMake or even Microsoft Visual Studio
  * Lack of pull and push centric deployment architectures.
    * Tools depend on shell-like protocols to deploy binaries which can be resource intensive and slow for massive deployments.
    * Pull architectures allow for servers to fetch their own binaries.
  * Clean artifacting of configurations out of binaries/scripts
    * uDeploy offers the concept of artifacts, which allows for composing deployments by combining versioned artifacts.
    * For instance, uDeploy allows for artifacting the following: 
      * binaries
      * database deployment/initialization scripts
      * configurations
  * Confusing structure and execution flow of deployments
    * Order is critical in deployment.
      * e.g. services can't start if the binaries for the service are not available yet.
    * Tools like Ansible and Puppet may not execute a set of tasks or roles in the order they are written, it's generally recommended one uses listeners and/or handlers and signal them to prevent ordering issues.

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

