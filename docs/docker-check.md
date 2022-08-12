# [docker-check]

This workflow is intended to inspect for codes that included inside docker image and dockerfile.

## Workflow main behavior

- Lint dockerfile w/ [hadolint]
- Lint docker image w/ [dockle]
- Scan vulnerability w/ [trivy]
  - (Optional) Update PR to comment results
  - (Optional) Create an issue if failure

## Usage

```yaml
    uses: koei-kaji/reusable-github-actions/.github/workflows/update-submodules.yaml@{ref}
    with:
      working-direcoty: "./path/to/dir/"
```

## Workflow inputs

| Name                  | Description                                                         | Default                       |
| --------------------- | ------------------------------------------------------------------- | ----------------------------- |
| `working-directory`   | Relative directory path under `GITHUB_WORKSPACE` to the repository. | `.`                           |
| `docker-tag`          | Docker tag tagged in the workflow.                                  | `docker-image:github-actions` |
| `docker-filename`     | Name of the Dockerfile.                                             | `Dockerfile`                  |
| `trivy-exit-code`     | Exit code when specified vulnerabilities are found.                 | `1`                           |
| `update-pull-request` | Whether to update PR to comment results of trivy.                   | `true`                        |
| `create-issue`        | Whether to create an issue if trivy was failure.                    | `false`                       |

## Workflow outputs

Nothing.  

## Examples

### Update PR

```yaml
  # ...
  plan-dev:
    uses: koei-kaji/reusable-github-actions/.github/workflows/docker-check.yaml@{ref}
    with:
      update-pull-request: true
  # ...
```

![img](./img/docker_check_update_pr.png.png)

### Create issue if trivy is in failure

```yaml
  # ...
  plan-dev:
    uses: koei-kaji/reusable-github-actions/.github/workflows/docker-check.yaml@{ref}
    with:
      create-issue: true
  # ...
```

![img](./img/../docker_check_create_issue.png)

## Actions built with

- [actions/checkout]
- [hadolint/hadolint-action]
- [aquasecurity/trivy-action]
- [actions/github-script]
- [JasonEtco/create-an-issue]

[docker-check]: ../.github/workflows/docker-check.yaml

[hadolint]: https://github.com/hadolint/hadolint
[dockle]: https://github.com/goodwithtech/dockle
[trivy]: https://github.com/aquasecurity/trivy

[actions/checkout]: https://github.com/marketplace/actions/checkout
[hadolint/hadolint-action]: https://github.com/marketplace/actions/hadolint-action?version=v2.0.0
[aquasecurity/trivy-action]: https://github.com/marketplace/actions/aqua-security-trivy
[actions/github-script]: https://github.com/marketplace/actions/github-script
[JasonEtco/create-an-issue]: https://github.com/marketplace/actions/create-an-issue