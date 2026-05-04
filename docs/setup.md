# Local Environment Setup

## Required Tooling

- Docker 26.x
- kubectl v1.30
- kind v0.22
- minikube v1.33
- Java 21
- Maven 3.9

## Local Repo Layout

Clone the split repositories as siblings:

```text
workspace/
|- app-build/
|- apps/
`- argocd/
```

The helper scripts in `app-build/scripts` resolve the `app` repo from that sibling layout.
