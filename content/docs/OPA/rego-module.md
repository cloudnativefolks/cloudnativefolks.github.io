---
title: "rego module"
weight : 4
---

#### Rego modules


Rego modules are used to express policies that can be enforced across a variety of software systems


```
package play

import data.servers
import data.networks

default allow = false

allow {
    some server
    servers[server]
    server.protocols["http"]
    network := networks[server.network]
    network.public
}

violation[{"id": server.id, "violation": "insecure-protocol"}] {
    server := servers[_]
    server.protocols["telnet"]
}

```


### Rego Module Explanation

This table provides an overview of the components in the provided Rego module.

| Component           | Explanation                                                                                           |
|---------------------|-------------------------------------------------------------------------------------------------------|
| `package play`      | Names the package as `play`. This namespace encapsulates the rules defined within the module.         |
| `import data.servers` | Imports data related to servers from an external source, making it available for policy evaluation.   |
| `import data.networks` | Imports network-related data, similar to the servers import, for use in policy decisions.            |
| `default allow = false` | Sets a default rule named `allow`. If no other rules are matched, the policy will deny access by default. |
| `allow { ... }`      | A rule named `allow`. It evaluates to `true` when specific conditions are met: when a server uses the HTTP protocol and is in a public network. |
| `violation[{"id": server.id, "violation": "insecure-protocol"}] { ... }` | Generates a set of objects representing policy violations. Each object includes the server's `id` and a string indicating the type of violation, such as using the insecure `telnet` protocol. |

Each of these components plays a critical role in defining and executing the policy as specified in the Rego language.




#### JSON Data Structure for OPA Policies

This section describes the JSON data structure used with Rego policies in Open Policy Agent (OPA). The data represents servers and networks, serving as input for policy evaluation.

##### Data Structure

### Servers
The `servers` object contains information about servers, each identified by a key (e.g., `s1`, `s2`). Each server has an `id`, is associated with a `network`, and supports various `protocols`.

```json
"servers": {
    "s1": {
        "id": "server1",
        "network": "n1",
        "protocols": ["http", "ssh"]
    },
    "s2": {
        "id": "server2",
        "network": "n2",
        "protocols": ["telnet"]
    }
}

```


Networks

The networks object provides details about different networks, specifying whether they are public.


```
"networks": {
    "n1": {
        "public": true
    },
    "n2": {
        "public": false
    }
}

```

### Usage in Rego Policies

allow Rule: This rule will evaluate to true for servers like s1 in the servers object, as it uses secure protocols (e.g., http) and is connected to a public network (n1).

violation Rule: This rule will identify servers like s2 in the servers object as violations, as it uses an insecure protocol (telnet).

```

➜  2 git:(main) ✗ opa eval --input data.json --data play.rego "data.play.allow"

{
  "result": [
    {
      "expressions": [
        {
          "value": false,
          "text": "data.play.allow",
          "location": {
            "row": 1,
            "col": 1
          }
        }
      ]
    }
  ]
}
➜  2 git:(main) ✗ opa eval --input data.json --data play.rego "data.play.violation"

{
  "result": [
    {
      "expressions": [
        {
          "value": [],
          "text": "data.play.violation",
          "location": {
            "row": 1,
            "col": 1
          }
        }
      ]
    }
  ]
}
➜  2 git:(main) ✗ 
```