---
title: "rego import statement"
weight : 4
---





the import statement is a fundamental feature that allows you to include definitions from other modules into your current module. This capability is crucial for organizing, reusing, and managing your policy code efficiently. Here's a brief explanation of how it works, along with an example:



In Rego, the policy language used by Open Policy Agent (OPA), the import statement is a fundamental feature that allows you to include definitions from other modules into your current module. This capability is crucial for organizing, reusing, and managing your policy code efficiently. Here's a brief explanation of how it works, along with an example:

Import Statement in Rego


Syntax: The basic syntax of an import statement in Rego is import <path>, where <path> is the path to the module or package you want to import.

Usage: When you import a package, you can use the functions, rules, and variables defined in that package in your current module. This helps avoid duplication of code and makes policies more modular and manageable.
Aliases: You can also assign aliases to imports for convenience or to avoid name conflicts. For example, import data.common.helpers as h allows you to refer to the contents of data.common.helpers using the alias h.

```
package common.helpers

default is_admin = false

# A simple rule to check admin status
is_admin {
    input.user == "admin"
}

```
helpers.rego 

main.rego 
```
package main

import data.common.helpers as h

# A rule that uses the imported is_admin rule
allow {
    h.is_admin  # Using the alias 'h' to refer to common.helpers
    # Additional conditions can be added here
}


```

The helpers.rego file defines a package common.helpers with a rule is_admin.
The main.rego file imports common.helpers with an alias h.
The allow rule in the main.rego file uses h.is_admin to utilize the is_admin rule from the imported module.


input.json

```
{"user": "admin"}
```

3 git:(main) ✗ opa eval --data helpers.rego --data main.rego --input input.json 'data.main.allow'         
    
{
  "result": [
    {
      "expressions": [
        {
          "value": true,
          "text": "data.main.allow",
          "location": {
            "row": 1,
            "col": 1
          }
        }
      ]
    }
  ]
}