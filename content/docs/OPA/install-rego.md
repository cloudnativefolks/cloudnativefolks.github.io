---
title: "Introduction to Rego"
weight : 2
---


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

> true = false
undefined
> true == false
false
> 3.14 > 3
true
> "hello" !="bye" 
true
> 


