---
layout: default
title: Catalog Push
nav_order: 3
parent: Actions
---

# Catalog Push Action

This action allows you to add an application to the Napptive Catalog.

## Napptive Catalog

The Napptive catalog is a collection of applications ready to be deployed. All users of the [Napptive Playground](https://playground.napptive.dev) have at their disposal the applications contained in the catalog.

The applications within the catalog are organized in different namespaces. You can upload apps to your account’s namespace. The application will be named as per the following notation: namespace/appName:tag.

To list all the available applications, execute:


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

* `applicationPath`

The path that contains the yaml files of the application to be uploaded. This input is **required**.

* `namespace`

The namespace where the application is going to be udpated. This input is **required**

* `applicationName`

With the name of the application.

* `tag`

With the application tag. If empty the application will be tagged as latest.

* `playgroundConfigFile`

This file allows you to change the target playground installation. This input is **not required**. Visit [documentation](https://docs.napptive.com/playground/On_premise_configuration.html#configuration-file) for an example.

---

## Example

```bash
{% raw %}name: Push an application to Napptive Playground
on: [push]
jobs:
  deploy:
    name: Catalog deploy
    runs-on: ubuntu-latest
    steps:
      name: Publish docker image, and update the application in the catalog
on: workflow_dispatch
env:
  PLAYGROUND_PAT: ${{ secrets.PLAYGROUND_PAT}}
jobs:
  build:
    name: Push docker images & deploy new version
    runs-on: ubuntu-latest
    steps:
            # Get a copy of the repo.
      - uses: actions/checkout@v2        
      - name: Push the application on the catalog
        uses: napptive-actions/catalog-push-action@v4.0.0
        with:
          applicationPath: ./build/k8s/
          namespace: "namespace"
          applicationName: "appName"
          tag: "v1.1.0"
{% endraw %}
```
