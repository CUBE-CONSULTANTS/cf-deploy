# CF CLI Action

Deploy to Cloud Foundry and manage your apps and services using the CF CLI v.8 easily with this GitHub Action.

# Pourpose

This action is intended to be used for build, if necessary, and deploy to SAP BTP Cloud Foundry Runtime with the CF CLI.

## 1. Build your App

The action executes the `cf` command with the provided arguments. 

You can use the `cf` command to build your app, if necessary. The command to build your app should be provided in the property `command_build` of action file.

## 2. Deploy to Cloud Foundry

The action executes the `cf` command with the provided arguments. The command to deploy your app should be provided in the property `command_deploy` of action file.

# Example Workflow
```
name: Build & Deploy to Cloud Foundry

on:
  push:
    branches:
    - master

jobs:    
    steps:
    - uses: CUBE-CONSULTANTS/cf-deploy@v0.0.1@master
      with:
        cf_api: https://api.my-cloud-foundry.com
        cf_username: ${{ secrets.CF_USER }}
        cf_password: ${{ secrets.CF_PASSWORD }}
        cf_org: AwesomeApp
        cf_space: Development
        command: push -f manifest-dev.yml
```

# Secrects

Copy `my.secret.sample` to `my.secret` and fill it with your credentials.

`cp my.secret.sample my.secret`

## Inputs

- CF_API=
- CF_USER=
- CF_PASSWORD=
- CF_ORG=
- CF_SPACE=

# Run in local

Use act to run the action in local. [act](https://github.com/nektos/act)

load secrets values from my.secrets file.
secrets file format is the same as .env format

`act --secret-file my.secrets`