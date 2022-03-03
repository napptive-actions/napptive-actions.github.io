---
layout: default
title: Playground action
nav_order: 1
parent: Actions
---

# Playground Github Action

This action allows you to execute the playground command you need.  

## Playground

Napptive playground simplifies the process to depoy and maintenance cloud-native applications. [Try for free!!](https://playground.napptive.dev)

---

## Environment Variables

* `PLAYGROUND_PAT`

The PLAYGROUND_PAT environment variable contains the Napptive [Personal Access Token](../index.md/#personal-access-token).

## Inputs

* `cmd`

The playground command to run. This input is **required**.

* `environment`

To specify the environment where the application is going to be deployed. If empty, the application will be deployed in the default environment.

* `playgroundConfigFile`

This file allows you to change the target playground installation. Visit [documentation](https://docs.napptive.com/playground/On_premise_configuration.html#configuration-file) for an example.

---

## Example

```bash
name: List deployed applications
on: [push]
jobs:
  deploy:
    name: Playground List applications
    runs-on: ubuntu-latest
    steps:
      # Get a copy of the repo.
      - uses: actions/checkout@v2
      # Execute `playground apps deploy .`.
      - uses: napptive-actions/playground-github-action@v2.2.1
        env:
          PLAYGROUND_PAT: ${{ secrets.PLAYGROUND_PAT }}
        with:
          cmd: "apps"
```

## References

* [Napptive Playground](https://playground.napptive.dev)
* [Napptive Documentation](https://docs.napptive.com/)
* [Napptive Web](https://napptive.com/)
