# node-code-check

This workflow is intended to inspect for node codes.  
It is assumed that using [volta] to fix node and npm version.

## Workflow main behavior

- Check format using given command
- Lint using given command
- Test using given command

## Usage

```yaml
    uses: koei-kaji/reusable-github-actions/.github/workflows/node-code-check.yaml@{ref}
    with:
      working-directory: "./path/to/dir/"
      command-check-format: "npm run format:check"
      command-lint: "npm run lint"
      command-test: "npm run test"
```

## Workflow inputs

| Name                   | Description                                                         | Default                |
|------------------------|---------------------------------------------------------------------|------------------------|
| `working-directory`    | Relative directory path under `GITHUB_WORKSPACE` to the repository. | `.`                    |
| `command-check-format` | Command to execute for checking format.                             | `npm run format:check` |
| `command-lint`         | Command to execute for linting.                                     | `npm run lint`         |
| `command-test`         | Command to execute for testing.                                     | `npm run test`         |

## Workflow outputs

Nothing.  

## Actions built with

- [actions/checkout]
- [volta-cli/action]
- [actions/cache]

[volta]: https://github.com/volta-cli/volta

[actions/checkout]: https://github.com/marketplace/actions/checkout
[volta-cli/action]: https://github.com/marketplace/actions/volta-cli-action
[actions/cache]: https://github.com/marketplace?type=actions&query=cache+