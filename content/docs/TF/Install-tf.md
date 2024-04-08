
---
title: "Install Terraform "
weight : 1
---

### Install brew 

```bash
brew tap hashicorp/tap
```
output 

```
==> Tapping hashicorp/tap
Cloning into '/opt/homebrew/Library/Taps/hashicorp/homebrew-tap'...
remote: Enumerating objects: 3830, done.
remote: Counting objects: 100% (595/595), done.
remote: Compressing objects: 100% (199/199), done.
remote: Total 3830 (delta 453), reused 510 (delta 396), pack-reused 3235
Receiving objects: 100% (3830/3830), 705.07 KiB | 1.45 MiB/s, done.
Resolving deltas: 100% (2489/2489), done.
Tapped 2 casks and 27 formulae (85 files, 969.9KB).

```

```
brew install hashicorp/tap/terraform
```

output 

```
brew install hashicorp/tap/terraform
==> Fetching hashicorp/tap/terraform
==> Downloading https://releases.hashicorp.com/terraform/1.6.3/terraform_1.6.3_darwin_arm64.zip
############################################################################################################################## 100.0%
==> Installing terraform from hashicorp/tap
🍺  /opt/homebrew/Cellar/terraform/1.6.3: 3 files, 84MB, built in 2 seconds
==> Running `brew cleanup terraform`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> `brew cleanup` has not been run in the last 30 days, running now...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
Removing: /Users/sangambiradar/Library/Caches/Homebrew/buf--1.25.1... (16.9MB)
Removing: /Users/sangambiradar/Library/Caches/Homebrew/cloudflared--2023.7.3.tgz... (16.8MB)
Removing: /Users/sangambiradar/Library/Caches/Homebrew/dart--3.0.7.zip... (187.2MB)
Removing: /Users/sangambiradar/Library/Caches/Homebrew/nuclei--2.9.10... (18.6MB)
Removing: /Users/sangambiradar/Library/Logs/Homebrew/dart-sass-embedded@1.62.1... (4 files, 2.6KB)
Removing: /Users/sangambiradar/Library/Logs/Homebrew/hugo... (64B)
Removing: /Users/sangambiradar/Library/Logs/Homebrew/localstack-cli... (125B)
Removing: /Users/sangambiradar/Library/Logs/Homebrew/dart... (115B)
Removing: /Users/sangambiradar/Library/Logs/Homebrew/nvm... (64B)
Removing: /Users/sangambiradar/Library/Logs/Homebrew/cloudflared... (129B)
```

### verify installation 

```
HashiCorp-Certified-Terraform-Associate git:(main) ✗ terraform -help
Usage: terraform [global options] <subcommand> [args]

The available commands for execution are listed below.
The primary workflow commands are given first, followed by
less common or more advanced commands.

Main commands:
  init          Prepare your working directory for other commands
  validate      Check whether the configuration is valid
  plan          Show changes required by the current configuration
  apply         Create or update infrastructure
  destroy       Destroy previously-created infrastructure

All other commands:
  console       Try Terraform expressions at an interactive command prompt
  fmt           Reformat your configuration in the standard style
  force-unlock  Release a stuck lock on the current workspace
  get           Install or upgrade remote Terraform modules
  graph         Generate a Graphviz graph of the steps in an operation
  import        Associate existing infrastructure with a Terraform resource
  login         Obtain and save credentials for a remote host
  logout        Remove locally-stored credentials for a remote host
  metadata      Metadata related commands
  output        Show output values from your root module
  providers     Show the providers required for this configuration
  refresh       Update the state to match remote systems
  show          Show the current state or a saved plan
  state         Advanced state management
  taint         Mark a resource instance as not fully functional
  test          Execute integration tests for Terraform modules
  untaint       Remove the 'tainted' state from a resource instance
  version       Show the current Terraform version
  workspace     Workspace management

Global options (use these before the subcommand, if any):
  -chdir=DIR    Switch to a different working directory before executing the
                given subcommand.
  -help         Show this help output, or the help for a specified subcommand.
  -version      An alias for the "version" subcommand.
➜  HashiCorp-Certified-Terraform-Associate git:(main) ✗ 

```