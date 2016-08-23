---
# ansible
---

3. Ansible and other Domain Specific Languages
==============================================

Ansible is one of the newer configuration management tools.
One of it's advantages over it's predecessors is that it is agent-less;
agent-less as in, it creates self-contained python payloads that is executes on the remote machine. 
This means less setup as other tools require a running service to manage and trigger jobs.
However, the one thing that makes them the same is how they all kind of work.

Ansible, like many of it's competitors: puppet, chef, uDeploy, etc; consume domain specific languages.
The domain specific language is then parsed and compiled (or interpreted) into some actionable set of instructions.
To make them more extensible, many of these tools allow for creating what are called modules;
These modules are written in a much more general programming language and are thus, more expressive, but theoretically harder to write for non-programmers.

Domain specific languages differentiate themselves from general purpose languages in the sense that their scope is significantly limited to a very specific problem.
The goal of this is to make it simpler to solve problems in a particular domain by doing less.
Generally, domain specific languages make use of simple grammars, like yaml, json, etc; to write in.
These languages have mature parsers in most general purpose languages like python, ruby and perl.
Thus, instead of writing a whole new language, generally one can fallback on these simpler languages and then generate the code using the structured output of the parsers.

Ansible for instance uses yaml syntax to describe "playbooks;" 
basically a set of instructions to execute on machines.
The yaml is parsed into a simple object that is a collection of key value pairs, where the values can be numbers, strings, boolean, objects or lastly, arrays of all of the other types.
From there, the ansible tool creates a python script by using the data contained in the parsed result.
Calls to modules and other such things in the parsed structure are replaced with literal python source.
Effectively, it's just a translation to library calls.
