---
layout: default
title: Catalog Deploy
nav_order: 2
parent: Actions
---

# Catalog Deploy Action

This action allows you to deploy an application from the Napptive Catalog.

## Napptive Catalog

The Catalog is a collection of applications ready to be deployed. All users of the [Napptive Playground](https://playground.napptive.dev) have the applications contained in the catalog at their disposal.

To list all available applications, execute:

```bash
$ playground login
Logged into account [account] - environment [environment]

$ playground catalog list
...
```

---

## Environment Variables

* `PLAYGROUND_PAT`

The PLAYGROUND_PAT environment variable contains the Napptive [Personal Access Token](../index.md/#personal-access-token).

## Inputs

* `appName`

With the name of the application to deploy. This input is **required**.

* `environment`

To specify the environment where the application is going to be deployed. If empty, the application will be deployed in the default environment.

* `playgroundConfigFile`

This file allows you to change the target playground installation. Visit [documentation](https://docs.napptive.com/playground/On_premise_configuration.html#configuration-file) for an example.

---

## Example

```bash
name: Deploy to Napptive Playground from Catalog
on: [push]
jobs:
  deploy:
    name: Catalog deploy
    runs-on: ubuntu-latest
    steps:
      # Deploying napptive/drawio:14.3.0 from the catalog
      - uses: napptive-actions/catalog-deploy-action@v2.4.1
        env:
          PLAYGROUND_PAT: ${{ secrets.PLAYGROUND_PAT }}
        with:
          appName: "napptive/drawio:14.3.0"
```
