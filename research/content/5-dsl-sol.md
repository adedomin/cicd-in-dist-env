---
# solutions
---

5. Domain Specific Language for Integration testing, Packaging and Deployment
=============================================================================

Below will be the explanation of a new DSL that I will develop that will attempt to solve shortfalls in other tools. 
Ideally, to also merge them into a universal testing, packaging and deployment framework.
The goal of the language is to solve the following.

  * Irreversibility of many configuration management tools.
  * Resolving build tool, and other environment specific dependencies
  * Lack of pull and push centric deployment architectures.
  * Clean artifacting of configurations out of binaries/scripts
  * Confusing structure and execution flow of deployments

DSL should feature:

  * Multi-paradigm for describing deployments
    * graphs (DOT language)
    * sequential steps (yaml|toml|json|etc)
  * Dependency management for playbooks & components
    * think npm, pip, etc.
  * Integration of all the key steps in a integration and deployment pipeline
    * Integration (testing)
    * Packaging (artifacting)
    * Deployment
  * "Agentless" service
    * Utilize builtins only
    * Scripting languages
