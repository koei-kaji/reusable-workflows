# docker-check

This workflow is intended to inspect for codes that included inside docker image and dockerfile.

## Workflow main behavior

- Lint dockerfile w/ [hadolint]
- Lint docker image w/ [dockle]
- Scan vulnerability w/ [trivy]

## Usage

```yaml
    uses: koei-kaji/reusable-github-actions/.github/workflows/update-submodules.yaml@{ref}
    with:
      working-direcoty: "./path/to/dir/"
```

## Workflow inputs

| Name                | Description                                                         | Default                       |
|---------------------|---------------------------------------------------------------------|-------------------------------|
| `working-directory` | Relative directory path under `GITHUB_WORKSPACE` to the repository. | `.`                           |
| `docker-tag`        | Docker tag tagged in the workflow.                                  | `docker-image:github-actions` |
| `docker-filename`   | Name of the Dockerfile.                                             | `Dockerfile`                  |

## Workflow outputs

Nothing.  

## Actions built with

- [actions/checkout]
- [hadolint/hadolint-action]
- [aquasecurity/trivy-action]

[hadolint]: https://github.com/hadolint/hadolint
[dockle]: https://github.com/goodwithtech/dockle
[trivy]: https://github.com/aquasecurity/trivy

[actions/checkout]: https://github.com/marketplace/actions/checkout
[hadolint/hadolint-action]: https://github.com/marketplace/actions/hadolint-action?version=v2.0.0
[aquasecurity/trivy-action]: https://github.com/marketplace/actions/aqua-security-trivy