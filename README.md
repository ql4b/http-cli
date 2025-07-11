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