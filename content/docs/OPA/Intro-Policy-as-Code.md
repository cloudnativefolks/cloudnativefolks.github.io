---
title: "Introduction to Policy as Code"
weight : 1
---

### Introduction To Policy as Code 

Within the domain of Information Technology, a policy is essentially a collection of rules, guidelines, or directives that govern the utilization of IT resources and the execution of operations. This might encompass, for instance, a series of conditions that code must satisfy to clear a security check and proceed to deployment. Alternatively, it might involve an authorization policy delineating the permissible access range for a given asset or resource.

Traditional methods of policy enforcement often embed authorization rules directly within the application, bypassing the benefits offered by a decoupled policy-as-code approach. Consequently, such policies lack the capability to be version-controlled or consistently replicated. Moreover, these conventional systems are not designed to accommodate policy testing, thereby creating obstacles in aligning with automated testing protocols.

### Install Rego on Mac 

```
➜  ~ curl -L -o opa https://openpolicyagent.org/downloads/v0.61.0/opa_darwin_amd64
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    81  100    81    0     0    271      0 --:--:-- --:--:-- --:--:--   270
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
100 60.4M  100 60.4M    0     0  12.6M      0  0:00:04  0:00:04 --:--:-- 24.3M
➜  ~ chmod 755 ./opa
➜  ~ curl -L -o opa_darwin_amd64 https://openpolicyagent.org/downloads/v0.61.0/opa_darwin_amd64
curl -L -o opa_darwin_amd64.sha256 https://openpolicyagent.org/downloads/v0.61.0/opa_darwin_amd64.sha256
shasum -c opa_darwin_amd64.sha256
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    81  100    81    0     0    570      0 --:--:-- --:--:-- --:--:--   574
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 60.4M  100 60.4M    0     0  13.8M      0  0:00:04  0:00:04 --:--:-- 24.5M
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    88  100    88    0     0    664      0 --:--:-- --:--:-- --:--:--   666
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100    83  100    83    0     0     35      0  0:00:02  0:00:02 --:--:--   192
opa_darwin_amd64: OK
➜  ~ 

➜  ~ chmod 755 ./opa
➜  ~ ./opa run
OPA 0.11.0 (commit e7a34319, built at 2019-05-21T06:30:19Z)

Run 'help' to see a list of commands.

> true 
true
> 3.14
3.14
> ["hello","Sangam"]
[
  "hello",
  "Sangam"
]

```

### if your using linux 

```
curl -L -o opa https://github.com/open-policy-agent/opa/releases/download/v0.11.0/opa_linux_amd64

```

### Boolen experession 

```
> true = false
undefined
> true == false
false
> 3.14 > 3
true
> "hello" !="bye" 
true
> 
```

