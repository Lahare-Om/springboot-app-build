# App Building Repo

This repo owns build automation, local helper scripts, and runbooks for the application platform.

## What Lives Here

- `.github/workflows/` for CI/CD automation
- `scripts/` for local cluster/bootstrap/smoke-test helpers
- `docs/` for setup and operational notes

## Expected Sibling Repositories

The local scripts assume this layout on disk:

```text
workspace/
|- app-build/
|- app/
`- argocd/
```

## GitHub Setup

Set these in the `app-build` GitHub repository before enabling the workflow:

- Repository variable `APPS_REPOSITORY`: `Lahare-Om/springboot-app`
- Secret `CROSS_REPO_TOKEN`: a token with permission to checkout and push to the app repo
- Secrets `DOCKER_USERNAME` and `DOCKER_PASSWORD`

For `CROSS_REPO_TOKEN`, use a GitHub token that can read and write `Lahare-Om/springboot-app` contents. The workflow needs this because it commits the updated Kubernetes image tag back to the app repo's `deploy` branch.

The root workflow builds the Spring Boot image from the checked-out `app` repo and updates `k8s/base/deployment.yaml` on the `deploy` branch.
