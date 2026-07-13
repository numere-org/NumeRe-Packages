# Contributing to NumeRe::Packages
Thank you for considering to contribute to the central package repository. This file describes the main need-to-knows for you. We recommend that you read it thoroughly.

## Process and Requirements
Because we want to ensure that all contributions are safe and have some kind of quality standard, we introduced the requirement for forking and the creation of pull requests as a desired friction. However, the process is not so different from Winget's approach, although there's more automation behind it. It goes as follows:

1. Fork this repository if you haven't already, otherwise sync your fork so that the main branch is up-to-date
2. Create a branch within your fork, i.e. `add_pkg_XYZ`
3. Push your package to your fork. Ensure that the folder structure is correct, i.e. `packages/pkg_XYZ/i.j.k/pkg_XYZ.nscr` with `i.j.k` referencing the version number of your package
4. Create a pull request within this repository with which you intend to merge your branch
5. Respond to our feedback. PRs with unresponded feedback are considered stale after 7 days and will be closed
6. Smile, once the pull request is accepted and the package is available in the official repository (*Note* that it may take *up to 20min* until NumeRe finds the new package. This is to keep the load on the REST API from exploding)

### Optional tool support
We provide a dedicated package `pkg_packaging_tools` to simplify this process on your end. Execute `install pkg_packaging_tools@NumeRe::Packages` in your NumeRe-Terminal to install it for your local distribution. *Note* that this does not free you from having a GitHub account. You also need a classic authtoken with [repo access](https://github.com/settings/tokens/new?description=NumeRe-Packages&scopes=repo&default_expires_at=none).

This package provides the command `packaging`, with which you can perform a complete submission via `packaging "PACKAGEFILE" -set mode="submit"` or only the preparation and copying to a custom repository, which has to be cloned locally: `packaging "PACKAGEFILE" -set mode="prepare" repo="PATH/TO/REPO/ROOT"`. In the former case, the plugin will ask for the GitHub access token on first run, then it will create a fork of the official package repository within your account, commit the files and create the PR in your name. If the fork already exists, it will sync it before committing any code.

### Why do we enforce that the package is part of this repository?
That's simply because we want to be sure what the users are downloading and that the contents of the referenced file match the reviewed file. That's different from Winget, but we do expect that this repository will stay a lot smaller in terms of contributions as well as byte size.

## Agreements
The following agreements and conditions apply:

1. Although the package repository is flagged as Apache-2.0 licenses, you can use any license you want. Note that too restrictive licensed may affect some users
2. If you contribute your package, you implicitly ensure that you have checked your package for any misbehavior and you ensured that all functionality is tested sufficiently
3. We do not take any responsibility for package behavior or security. If we note any misbehavior, we will immediately remove the package and report the original comitter
4. All packages in this repository need to have a license, an author, a version and at least a description
5. Any contributions are locked in their version. We do not accept any edit PRs. If you want to change the contents of a specific version of your package, request for a deletion first. We do however recommend to release a new version instead
