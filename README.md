
# http-cli

A shell script that acts like a teammate.

`http-cli` is a minimal yet powerful Bash-based HTTP client built around `curl`, designed to be quiet by default, expressive when needed, and easily composable in scripting environments.

## Features

- Supports custom methods, headers, and body formats (JSON, form-encoded, files)
- Cookie jar management and proxy support
- Configurable timeout, verbosity, and engine flags
- Inline or file-based configuration via `~/.http-cli.conf`
- Optional header and status code dumping
- Clean CLI interface and easily extendable design

## Usage examples

```bash
http-cli https://httpbin.org/robots.txt
```

```bash
http-cli --user-agent "http-cli/0.1 (https://github.com/ql4b/http-cli)" \
    https://httpbin.org/user-agent
```

```bash
http-cli --dump-header - --status-codes \
    https://httpbin.org/status/204
```

## Full help

```
http-cli --help
```

## Configuration

You can define default settings in `~/.http-cli.conf`:

```
USER_AGENT="http-cli/0.1 (https://github.com/ql4b/http-cli)"
TIMEOUT=10
```

## Release Strategy

This project uses [semantic-release](https://semantic-release.gitbook.io/) to automate versioning and changelog generation.

- Commits to `main` trigger **stable releases** (e.g. `v1.2.3`)

Releases are based on [Conventional Commits](https://www.conventionalcommits.org/), so use commit messages like:
- `feat: add new feature`
- `fix: correct bug`
- `chore: update metadata`

## Development Workflow

Start from `main` your feature branch as in

```
git fetch origin
git switch -c feat/something origin/main
```

Make your changes and any commit to the feature branch as you wish.

When you are ready to promote your changes to main, from your local branch:

```
git switch main
git pull --rebase origin main
git switch feat/something
git rebase -i main
```

Add you fixups and edit the first commit message in a way that it represents your PR intent (`chore:`, `fix:`, `feat:` etc).

Now you push your feature branch and create the PR against `main`

```
git push -u origin feat/something
```

## Release Workflow

To publish your changes open a PR and wait for a review before merge.
