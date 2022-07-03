# submodules-update

This workflow is intended to update submodules.  
If we want to update submodules of private repository, we can update it easily by using this with GitHub App id and private key.  

## Workflow main behavior

- Get GitHub App token if necessary
- Update submodules, commit and push automatically

## Usage

```yaml
    uses: koei-kaji/reusable-github-actions/.github/workflows/submodules-update.yaml@{ref}
    secrets:
      app-id: ${{ secrets.APP_ID }}
      private-key: ${{ secrets.PRIVATE_KEY }}
```

## Workflow secret inputs

| Name          | Description             |
|---------------|-------------------------|
| `token`       | GitHub token.           |
| `app-id`      | GitHub App ID.          |
| `private-key` | GitHub App Private Key. |

## Workflow inputs

Nothin.

## Workflow outputs

Nothing.  

## Actions built with

- [getsentry/action-github-app-token]
- [actions/checkout]

[getsentry/action-github-app-token]: https://github.com/marketplace/actions/
[actions/checkout]: https://github.com/marketplace/actions/checkout
