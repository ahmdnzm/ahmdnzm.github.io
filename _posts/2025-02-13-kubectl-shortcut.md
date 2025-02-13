---
title: Kubectl Shortcut
date: 2024-08-01 12:00:00 +0800
categories: [Kubernetes]
tags: [linux, bash, kubernetes]     # TAG names should always be lowercase
---
# Kubectl Shortcut

- create an alias that shortens `kubectl` to `k`
- Ensures that the `k` alias also supports auto-completion, just like the full `kubectl` command.
- Persist the Alias and Autocompletion

```bash
echo 'alias k=kubectl' >> ~/.bashrc
echo 'source <(kubectl completion bash)' >> ~/.bashrc
echo 'complete -o default -F __start_kubectl k' >> ~/.bashrc
source ~/.bashrc
```