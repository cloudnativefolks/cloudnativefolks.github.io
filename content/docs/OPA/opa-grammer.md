---
title: "Open Policy Agent (OPA) Grammar"
weight : 2
---



# Open Policy Agent (OPA) Grammar

 the grammar used in Open Policy Agent (OPA) for writing policies. This grammar is expressed in Extended Backus-Naur Form (EBNF).

## Grammar Components

| Component         | Description                                                           |
|-------------------|-----------------------------------------------------------------------|
| `module`          | A collection of policies, includes package and policy definitions.    |
| `package`         | Defines the namespace for policies. Identified by a reference.        |
| `import`          | Imports definitions from another package, optionally with an alias.   |
| `policy`          | A set of rules that define the policy.                                |
| `rule`            | A unit in a policy, can be default, with a head and a body.           |
| `rule-head`       | Declarative part of a rule, includes name, arguments, and assignment. |
| `rule-body`       | Procedural part of the rule, consisting of a query.                   |
| `query`           | A series of literals representing conditions or facts.                |
| `literal`         | A basic unit in a query, can be a declaration, expression, or negation.|
| `expr`            | An expression, can be a term, function call, or infix operation.      |
| `term`            | The simplest unit, can be various types like reference, array, object.|
| `infix-operator`  | Operators for boolean, arithmetic, or binary operations.              |

This table provides a simplified overview of each component in the OPA grammar. The EBNF format is more detailed and specific, primarily used for implementing parsers and compilers. 


