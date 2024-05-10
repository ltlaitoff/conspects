---
title: How fe+be works
created: 2024-05-09 13:20
last modified: Thursday 9th May 2024 13:20:35
aliases: 
tags: []
---
# How fe+be works and how to test it

This documentation describes how the interaction of frontend and backend works in different environments, as well as how to test it.

## Frontend

On the `frontend`, we have 4 main environments (you can think of it as branches in git):
- `release` - This is the deployed version, i.e., our `production`, which uses the `production` version of `backend`
- `staging` - Pre-release version, can use `staging` or `production` versions of `backend`
- `dev` - Development version, can use `dev`, `staging`, or `production` versions of `backend`
- `feature/bug/other` - Pull requests

### How to test the required version of `backend`

To test the required version of `backend`, you need to do the following steps:
1. Switch to the required branch in `git`
2. Change `environment variables` to work with the required version of backend (local or remote)
3. Run `backend` locally (if necessary)
4. Run `frontend` in one of two ways:
	1. Locally in `development` mode. Execute the command `npm run dev`
	2. Locally in `production` mode. Delete the `dist` directory, execute the command `npm run build`, then `npm run preview`

### Release

The `frontend` release version is the most stable version that should work with the most stable `backend` version, i.e., with `release`.

Both `frontend` and `backend` release versions are deployed on the same domain.

#### How to test it?

Go to the deploy and test through it.

#### Can I, if necessary, use a different `backend` version?

Yes, but locally. Go to the `release` branch, and then follow the guide.

### Staging

`Staging` represents a new version of `frontend`. The new `frontend` version may either depend on a new `backend` version (for example, we have some new functionality), or it may be independent (we did something on `frontend` regardless of `backend`).

Both `frontend` and `backend` staging versions are not deployed anywhere yet.

#### How to test it?

There are two options:
1. If there is no need to change the `backend` version, you need to run the `docker image` provided by the developers. This option is more preferable because this `image` will then be in `release` if everything is fine.
2. If you need to change the `backend` version. Here you need to go to the branch locally, and then follow the guide.

### Dev

`Dev` - a version that is currently under development, which may not work, or work a bit crookedly

This version contains the latest changes that can be made at all

You can also use any version of `backend` here

#### How to test this?

Just go to the branch and run it

### feature/bug/other

`feature/bug/other` - These are our pull requests

Depending on which branch they go to, they need to be tested differently

If the PR goes to `dev` - test from `backend` used on `dev`

If the PR goes to `staging` - test from `backend` used on `staging`

If the PR goes to `release` - test like `staging`

## Backend

// TODO

Versions:
- `release`
- `staging`
- `dev`
