---
title: "Open Policy Agent (OPA) Grammar"
weight : 2
---

### Open Policy Agent (OPA) Grammar

 the grammar used in Open Policy Agent (OPA) for writing policies. 

### Grammar Components

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

This grammar is expressed in Extended Backus-Naur Form (EBNF).

```
module          = package { import } policy
package         = "package" ref
import          = "import" package [ "as" var ]
policy          = { rule }
rule            = [ "default" ] rule-head { rule-body }
rule-head       = var [ "(" rule-args ")" ] [ "[" term "]" ] [ = term ]
rule-args       = term { "," term }
rule-body       = [ else [ = term ] ] "{" query "}"
query           = literal { ";" | [\r\n] literal }
literal         = ( some-decl | expr | "not" expr ) { with-modifier }
with-modifier   = "with" term "as" term
some-decl       = "some" var { "," var }
expr            = term | expr-built-in | expr-infix
expr-built-in   = var [ "." var ] "(" [ term { , term } ] ")"
expr-infix      = [ term "=" ] term infix-operator term
term            = ref | var | scalar | array | object | set | array-compr | object-compr | set-compr
array-compr     = "[" term "|" rule-body "]"
set-compr       = "{" term "|" rule-body "}"
object-compr    = "{" object-item "|" rule-body "}"
infix-operator  = bool-operator | arith-operator | bin-operator
bool-operator   = "=" | "!=" | "<" | ">" | ">=" | "<="
arith-operator  = "+" | "-" | "*" | "/"
bin-operator    = "&" | "|"
ref             = var { ref-arg }
ref-arg         = ref-arg-dot | ref-arg-brack
ref-arg-brack   = "[" ( scalar | var | array | object | set | "_" ) "]"
ref-arg-dot     = "." var
var             = ( ALPHA | "_" ) { ALPHA | DIGIT | "_" }
scalar          = string | NUMBER | TRUE | FALSE | NULL
string          = STRING | raw-string
raw-string      = "`" { CHAR-"`" } "`"
array           = "[" term { "," term } "]"
object          = "{" object-item { "," object-item } "}"
object-item     = ( scalar | ref | var ) ":" term
set             = empty-set | non-empty-set
non-empty-set   = "{" term { "," term } "}"
empty-set       = "set(" ")"
```
