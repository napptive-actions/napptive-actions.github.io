---
layout: default
title: Actions
nav_order: 1
has_children: true
---

# NAPPTIVE Github Actions

Helping developers focus on creating awesome applications by facilitating the implementation of their workflows.

Napptive’s Github actions allows you to define workflows in a very simple way.

You will be able to quickly prepare a test environment by deploying the catalog applications you need, upload your code to the catalog to always have the latest version of your application available, update a deployed application, etc.

All of these tasks and many more will become very simple with the Napptive Github actions.

## Prerequisites

### Napptive Account

- You will need a Napptive Account. [It's free!!](https://playground.napptive.dev).

### Playground client

- Install the playground cli. Follow the instructions in the [documentation](https://docs.napptive.com/playground/Installation.html) on how to install.

### Personal Access Token

- The actions require a Personal Access Token (PAT) to log into the platform. Follow the [documentation](https://docs.napptive.com/guides/Using_personal_access_tokens.html) to create one. With the CLI, execute:

```bash
playground user pat create github-actions
Current environment: account/environment
NAME              TOKEN
github-actions    <PAT>

Please store this value safely as it cannot be retrieved once generated. To login with this value,...
```

and create a new Github Secret with the PAT.
_Settings -> Secret -> Actions -> New Repository secret_

![GitHub Secret](./images/github-secret.png)
