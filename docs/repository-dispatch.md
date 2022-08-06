# [repository-dispatch]

This workflow is intended to send the dispatch.  
This workflow is using great useful workflow: [peter-evans/repository-dispatch] almost as it is.
But we can use it to send the dispatch to private repository easily.  

## Workflow main behavior

- Get GitHub App token if necessary
- Send the dispatch repository

## Usage

```yaml
    uses: koei-kaji/reusable-github-actions/.github/workflows/repository-dispatch.yaml@{ref}
    secrets:
      app-id: ${{ secrets.APP_ID }}
      private-key: ${{ secrets.PRIVATE_KEY }}
    with:
      repository: owner/repository-name
      event-type: hello
      client-payload: '{"hello": "world"}'
```

## Workflow secret inputs

| Name          | Description             |
| ------------- | ----------------------- |
| `token`       | GitHub token.           |
| `app-id`      | GitHub App ID.          |
| `private-key` | GitHub App Private Key. |

## Workflow inputs

| Name             | Description                                                                                       | Default |
| ---------------- | ------------------------------------------------------------------------------------------------- | ------- |
| `repository`     | The full name of the repository to send the dispatch.                                             | -       |
| `event-type`     | A custom webhook event name.                                                                      | -       |
| `client-payload` | JSON payload with extra information about the webhook event that your action or workflow may use. | `{}`    |

## Workflow outputs

Nothing.  

## Actions built with

- [getsentry/action-github-app-token]
- [actions/checkout]
- [peter-evans/repository-dispatch]

[repository-dispatch]: ../.github/workflows/repository-dispatch.yaml

[peter-evans/repository-dispatch]: https://github.com/marketplace/actions/repository-dispatch?version=v2.0.0
[getsentry/action-github-app-token]: https://github.com/marketplace/actions/action-github-app-token
[actions/checkout]: https://github.com/marketplace/actions/checkout
