---
title: "rego policy rule"
weight : 5
---

the syntax `policy = { rule }` appears to be part of a grammar definition, possibly for a policy language like Open Policy Agent (OPA). In this context, 


### let's break it down:

policy: This typically represents the policy object or entity being defined. In the context of OPA, a policy is a set of rules and logic that defines the expected behavior or constraints in a particular system.

{ rule }: The curly braces {} indicate a block of content, and rule within them suggests that a policy consists of one or more rules. Each rule is a specific statement or logic that contributes to the overall policy.

In OPA, rules are fundamental components that produce decisions. A rule can take inputs (like user data, action types, etc.) and produce an output decision (like allow/deny, a score, a new data object, etc.).

### Example of OPA Policy

Let's consider a simple example to illustrate this. Suppose we want to define a policy for access control in a system:

create access-control.rego
```

package example

# Define a default decision
default allow = false

# Rule for allowing access
allow {
    input.user == "admin"
}

# Another rule for allowing access
allow {
    input.user == "user"
    input.action == "read"
}




```


create file input.json
```
{
    "user": "user",
    "action": "read"
}

```

In this example:

package example: This line names the policy package, a way to group and namespace the rules.
default allow = false: Sets the default decision for allow to false. This means if none of the rules for allow match, the policy will deny access.

The first allow rule allows access if the input user is "admin".
The second allow rule allows access if the input user is "user" and the action they are trying to perform is "read".

This policy can be queried with an input, and it will evaluate the rules based on that input to produce a decision (in this case, whether to allow or deny access).

OPA policies are powerful because they can be written to evaluate complex logic and handle a wide variety of input structures, making them suitable for a range of policy decision-making needs in software systems.


```
4 git:(main) ✗ opa eval --format pretty --data access-control.rego --input input.json 'data.example.allow'

true

```

