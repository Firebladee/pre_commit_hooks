[![Build Status](https://travis-ci.com/Firebladee/pre_commit_hooks.svg?branch=master)](https://travis-ci.com/Firebladee/pre_commit_hooks)
[![Coverage Status](https://coveralls.io/repos/github/Firebladee/pre_commit_hooks/badge.svg?branch=master)](https://coveralls.io/github/Firebladee/pre_commit_hooks?branch=master)

# Pre-commit hooks

Git hooks to integrate with [pre-commit](http://pre-commit.com).

## Configure pre-commit

Add to `.pre-commit-config.yaml` in your git repo.

    - repo: https://github.com/Firebladee/pre_commit_hooks
      rev: master
      hooks:
        - id: shellcheck
        - id: shellcheck_docker

## Two ways to invoke pre-commit

If you want to invoke the checks as a git pre-commit hook, run:

    pre-commit install

If you want to run the checks on-demand (outside of git hooks), run:

    pre-commit run --all-files --verbose

## Available hooks

### `shellcheck`

**What it does**

Run shellcheck against scripts.

**More info**

This hook uses the `identify` library of pre-commit to identify shell scripts.
If the file is a shell script, then run shellcheck against the file.

By default, this hooks passes `-e SC1091` to shellcheck.
Override locally with the `args` parameter in `.pre-commit-config.yaml`.

:warning: The `shellcheck` hook requires
[shellcheck](https://github.com/koalaman/shellcheck).

### `shellcheck_docker`

**What it does**

Run shellcheck using a docker instance of shellcheck against your scripts.

**More info**

This hook uses the `identify` library of pre-commit to identify shell scripts.
If the file is a shell script, then run shellcheck against the file.
