# pushing-docker-to-gcr

This workflow is intended to push docker image to Google Container Registry.  
It is assumed that using workload identity federation.  

## Workflow main behavior

- Authenticate to Google Cloud by workload identity federation
- Build the docker image
- Push the docker image

## Usage

```yaml
    uses: koei-kaji/reusable-github-actions/.github/workflows/pushing-docker-to-gcr.yaml@{ref}
    with:
      working-directory: "./path/to/dir/"
      docker-tag: "docker-image:${{ github.sha }}"
    secrets:
      workload-identity-provider: ${{ secrets.WORKLOAD_IDENTITY_PROVIDER }}
      service-account: ${{ secrets.SERVICE_ACCOUNT }}
      project-id: ${{ secrets.GCP_PROJECT_ID }}
      registry-host: ${{ secrets.GCP_REGISTRY_HOST }}
```

## Workflow secret inputs

| Name                         | Description                                           |
|------------------------------|-------------------------------------------------------|
| `workload-identity-provider` | See [google-github-actions/auth:action.yml].          |
| `service-account`            | See [google-github-actions/auth:action.yml].          |
| `project-id`                 | GCP Project ID.                                       |
| `registry-host`              | Google Container Registry Host, for example: `gcr.io` |

## Workflow inputs

| Name                | Description                                                         | Default      |
|---------------------|---------------------------------------------------------------------|--------------|
| `working-directory` | Relative directory path under `GITHUB_WORKSPACE` to the repository. | `.`          |
| `docker-tag`        | Tag of the docker image.                                            | -            |
| `dockerfile-name`   | Name of the Dockerfile.                                             | `Dockerfile` |

## Workflow outputs

Nothing.  

## Actions built with

- [actions/checkout]
- [google-github-actions/auth]
- [google-github-actions/setup-gcloud]

[google-github-actions/auth:action.yml]: https://github.com/google-github-actions/auth/blob/95a6bc2a27ae409a01ea58dd0732eccaa088ec07/action.yml

[actions/checkout]: https://github.com/marketplace/actions/checkout
[google-github-actions/auth]: https://github.com/marketplace/actions/authenticate-to-google-cloud
[google-github-actions/setup-gcloud]: https://github.com/marketplace/actions/set-up-gcloud-cloud-sdk-environment