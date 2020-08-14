# Linchpin Github Action Workflows

Default Workflows for new website projects being deployed (typically to WP Engine).

*Any globally beneficial changes should be made to these workflows.*

When changes are made they should be noted in the changelog within this readme and a release should be created of the same version #

[![Project Status: Active](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)

# Getting Started

## What is a workflow and how do I use it?

Worksflows are part of github's deployment process. At Linchpin we use workflows to deploy code to our development, staging and production environments. In order to utilize these workflows within your own projects you should add the appropriate workflow.yml file into a folder named `.github/workflows/` within your repo.

## Environment Deployment Workflow Differences

Each environment will have slightly different deployment workflows. For example develop and staging do not need to create "releases". All environment specific workflows should be documented accordingly within this readme.md or within the Wiki of this repo.

* * *

# Setting up a new repository

## Production
* Deploying to production **requires** a `v1.2.3` "semver" style tag after code is merged into the `master` branch.
* Pushing code to `master` alone will not create a deployment or release

### Production Deployment Steps

1. Merge or Pull Request into `master` branch
2. Tag the latest commit in the timeline you are looking to deploy with a "semver" style tag Example: `v1.2.3`
    Note: that this release number may vary from your plugin and/or theme version numbers. They are not dependent on one another
3. Be sure to push your tag to **"origin"**.
4. Once the tag is pushed to "origin", the build and deploy process will begin
5. A release is created of that point in time within the github repo
6. Composer dependencies are installed
7. Yarn or NPM dependencies are installed
8. Production build process is run
8. Codebase is deployed to production environment

## Staging
* Staging currently does not require a `v1.2.3` "semver" style tag in order to build and deploy code to the staging environment.
* Pushing to staging **will not** create a release.

# Changelog

## 1.0.3

* Added Slack notifications on start, complete, and fail.
* Added variables for site URL and site image URL

## 1.0.2

* Files are now compressed before deploying to the server
* Uses the .distignore file to clean up build files before deploying to the server

## 1.0.1

* Added a deployment yaml for production deploy-production.yml
* Removed the release creation from deploy-staging.yml only production should create a release

## 1.0.0

* Added the baseline deploy-staging.yml
