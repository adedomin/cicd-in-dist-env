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

6.1. Continuous Integration Domain
-----------------------------------

6.2. Configuration Management Domain
------------------------------------

![Example Workflow Proposal[^cm]](media/cm.png)

[^cm]: The idea behind this, is instead of pushing plaintext configurations and basic templating, users can develope parsers for various software configs or derive them from the community. The parsers would allow for dynamic configuration to occur in a clean way. It would also allow for more advanced querying.
