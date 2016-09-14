---
# comments go here
---

6. Domain Specific Languages (DSL)
==========================================

  * DSL
    * Limited scope, easy to solve singular task
    * Composed into general languages
    * Obfuscated library calls
    * Similar to PHP's origin
  * Challenges
    * scope creep
    * defining a encompassing scope for the problem domain
    * Adding logic to DSL

![CI language domain[^ci-domain]](media/ci-domain.png)

[^ci-domain]: graph that shows wha the Domain Specific language must solve in CI space.

6.1. Continuous Integration Domain
-----------------------------------

##  Key domain concepts
  * shell driven interactions
  * fork() and exec() of build tools.
  * managing environment variables
  * provisioning services, such as databases for testing purposes

Most of the problems in this domain boil down to shell script execution and interactions.
Secondary problem is resolving dependencies for services, like databases; and build tools like gradle.

6.2. Configuration Management Domain
------------------------------------

The final domain of the CICD process is configuration and maintenance.
This portion is more of a optional "agent-less" manager.
In this domain, the key problem is generating configuration files, and at a later time, able to regenerate them using newer information.
Currently to solve this problem, configuration management tools (and by extension, continuous deployment tools) offer the ability to take a structured document and apply the values therein to a general template.

![Example Workflow Proposal[^cm]](media/cm.png)

[^cm]: The idea behind this, is instead of pushing plaintext configurations and basic templating, users can develope parsers for various software configs or derive them from the community. The parsers would allow for dynamic configuration to occur in a clean way. It would also allow for more advanced querying.
