---
title: "rego terms"
weight : 6
---


a term is indeed a fundamental building block. Terms can represent various data structures, including scalar values, arrays, objects, sets, and comprehensions. Let's go through each of these, providing examples to illustrate their use in Rego.

- Scalar Values : Scalar values in Rego include types like numbers, strings, and booleans.

```
Numbers: 42, 3.14
Strings: "hello", "world"
Booleans: true, false

```
- Arrays:Arrays are ordered collections of terms.

```
["apple", "banana", "cherry"]

```
- Objects : Objects in Rego are collections of key-value pairs. The keys are always strings.

```
{"name": "sangam", "age": 27, "member": true}

```
- Sets : Sets are unordered collections of unique values.

```
{"red", "green", "blue"}

```

- Comprehensions : Rego allows for array, object, and set comprehensions, which are ways to define a collection based on existing collections.

Array Comprehensions: Generate an array based on some logic.

```
[x | x in [1, 2, 3, 4, 5]; x > 3]

```
This creates an array of numbers greater than 3 from the given list [1, 2, 3, 4, 5], resulting in [4, 5].

Object Comprehensions: Similar to array comprehensions, but for objects.

```
{x: y | x in ["a", "b", "c"]; y = upper(x)}

```

Assuming upper is a function that converts a string to uppercase, this comprehension would result in {"a": "A", "b": "B", "c": "C"}.

Set Comprehensions: Generate a set based on some logic.

```
{x | x in [1, 2, 3, 4, 5]; x % 2 == 0}

```




create file `user_permissions.rego`


```
package permissions

# Scalar values for roles
role_admin = "admin"
role_user = "user"

# Object mapping roles to allowed actions
actions_allowed = {
    role_admin: ["create", "read", "update", "delete"],
    role_user: ["read"]
}

# Main policy rule: Allow action
allow {
    # Set comprehension to generate the set of allowed actions for the user's role
    action_allowed := {action | action = actions_allowed[input.role][_]}
    # Check if the input action is in the set of allowed actions
    input.action == action_allowed[_]
}
```
- Package Declaration: package permissions - This declares the namespace for the policy.
- Scalar Values: role_admin and role_user are defined as constants representing user roles.
- Object Mapping: actions_allowed - This is an object mapping roles to arrays of allowed actions. It maps the role_admin and role_user roles to their respective allowed actions.
- Policy Rule allow:
The allow rule is the primary rule that determines whether an action is permitted based on the user's role.
- Set Comprehension: Inside the allow rule, a set comprehension (action_allowed) is used to create a set of actions allowed for the user's role, as specified in the input.
- Action Check: The policy then checks if the input.action is present in the action_allowed set.

create file input.json 

```
{
    "role": "admin",
    "action": "create"
  }
  
```


run opa 

```
opa eval -i input.json -d user_permissions.rego 'data.permissions.allow'

{
  "result": [
    {
      "expressions": [
        {
          "value": true,
          "text": "data.permissions.allow",
          "location": {
            "row": 1,
            "col": 1
          }
        }
      ]
    }
  ]
}

```

 evaluate whether the specified action ("create") is allowed for the given role ("admin"), according to the policy rules.