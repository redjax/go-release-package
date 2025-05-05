# Go Release Package

An example repository the demonstrates versioning & releasing Go packages.

## Setup

This repository expects a branch named `release` or `release/**` to exist. The pipeline runs on any merge from `main` into a `release` or `release/**` branch.

Use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) in your commit messages to trigger a release.

## Usage

The [release Github Action](./.github/workflows/release.yml) will trigger on any pull request into the `release` branch. The pipeline will use the commit history to determine the release type.

This means you must use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) to get the pipeline to trigger. Use the table below to help with commit messages for compatibility with a release pipeline:

| Commit message type           | Triggers release type   |
| ----------------------------- | ----------------------- |
| `fix:`                        | Patch (0.0.x → 0.0.x+1) |
| `feat:`                       | Minor (0.0.x → 0.1.0)   |
| `BREAKING CHANGE:` or `!`     | Major (0.x.x → 1.0.0)   |
| Other / no conventional style | No release              |

When writing a commit message, use one of the `Commit message type` syntaxes to trigger a release when `main` is merged into `release`. For example, to bump the minor (`0.0.x`) version, write a commit message like:

```shell
git commit -m "fix: Some minor change"
```
