# python-code-check

This workflow is intended to inspect for python codes.  
It is assumed that using [poetry].  

## Workflow main behavior

- Checking format using given command
- Lint using given command
- Test using given command

## Usage

```yaml
    uses: koei-kaji/reusable-github-actions/.github/workflows/python-code-check.yaml@{ref}
    with:
      python-version: "3.10.5"
      pip-version: "22.1.2"
      poetry-version: "1.1.13"
      working-directory: "./test_stubs/python/"
      command-check-format: "make format-check"
      command-lint: "make lint"
      command-test: "make test"
```

## Workflow inputs

| Name                   | Description                                                         | Default  |
|------------------------|---------------------------------------------------------------------|----------|
| `python-version`       | Python version.                                                     | -        |
| `poetry-version`       | Poetry version                                                      | `latest` |
| `working-directory`    | Relative directory path under `GITHUB_WORKSPACE` to the repository. | `.`      |
| `command-check-format` | Command to execute for checking format.                             | -        |
| `command-lint`         | Command to execute for linting.                                     | -        |
| `command-test`         | Command to execute for testing.                                     | -        |

## Workflow outputs

Nothing.  

## Actions built with

- [actions/checkout]
- [actions/setup-python]
- [snok/install-poetry]
- [actions/cache]

[poetry]: https://github.com/python-poetry/poetry

[actions/checkout]: https://github.com/marketplace/actions/checkout
[actions/setup-python]: https://github.com/marketplace/actions/setup-python
[snok/install-poetry]: https://github.com/marketplace/actions/install-poetry-action
[actions/cache]: https://github.com/marketplace?type=actions&query=cache+
