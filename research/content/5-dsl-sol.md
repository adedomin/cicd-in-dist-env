---
# solutions
---

5. Domain Specific Language for Integration testing, Packaging and Deployment
=============================================================================

Below will be the explanation of a new DSL that I will develop that will attempt to solve shortfalls in other tools. 
Ideally, to also merge them into a universal testing, packaging and deployment framework.
The goal of the language is to solve the following.

  * Irreversibility of many configuration management tools.
    * Many of the tools in use make untracked, and ultimately, difficult to revert, changes to the filesystem.
    * Tools should track needed changes to the filesystem so that they can be removed and cleaned up or possibly updated later.
    * Many devops manuals expect you to do A-B deployments to prevent this issue.
      * A and B as in, when a new deployment needs to occur, build a new machine to deploy to and if it breaks, bring back the old machine.
      * Some systems take it to the extreme by having the OS be an immutable source tree which is entirely redeployed or reverted on changes.
  * Resolving build tool, and other environment specific dependencies
    * There a various tools for languages like java: gradle, maven, ant, etc.
    * These tools may not be installed on the CI server.
    * To work around this, gradle and maven offer "wrapper" scripts.
      * This requires your project to ship with a gradle or maven java binary.
    * In C/C++, people could be using GNU Autoconf, CMake or even Microsoft Visual Studio
  * Lack of pull and push centric deployment architectures.
    * Tools depend on shell-like protocols to deploy binaries which can be resource intensive and slow for massive deployments.
    * Pull architectures allow for servers to fetch their own binaries.
  * Clean artifacting of configurations out of binaries/scripts
    * uDeploy offers the concept of artifacts, which allows for composing deployments by combining versioned artifacts.
    * other tools do not.
  * Confusing structure and execution flow of deployments
    * Tools like Ansible and Puppet may not execute a set of tasks or roles in the order they are written, it's generally recommended one uses listeners and/or handlers and signal them to prevent race conditions.

DSL should feature:

  * Multi-paradigm for describing deployments
    * graphs (Metamodeling - or Model driven)
      * Ideally with a drawing tool
      * Alternatively, users could make graphs using the DOT language, or another simplier graph language
    * sequential steps (yaml|toml|json|etc)
      * similar to ansible, puppet and many others.
  * Dependency management for playbooks & components
    * think npm, pip, etc.
    * requires playbooks and components have a package file that describes what they provide.
  * Integration of all the key steps in a integration and deployment pipeline
    * Integration (testing)
    * Packaging (artifacting)
    * Deployment
    * Configuration Management
  * "Agentless" service
    * Utilize builtins only
    * Scripting languages
