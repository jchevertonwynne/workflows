# workflows

Reusable GitHub Actions workflows shared by the apps running on the k3s
cluster described in `jchevertonwynne/homelab`.

Public because a private repo's reusable workflows need per-repo access
configuration to be callable, and there is nothing sensitive in here.

## build-image.yml

Builds a `linux/arm64` image and pushes it to GHCR with the three tags Flux
image automation expects. Call it from an app repo:

```yaml
name: Image
on:
  push:
    branches: [main]
    paths-ignore: ["**.md"]
  workflow_dispatch:

jobs:
  image:
    uses: jchevertonwynne/workflows/.github/workflows/build-image.yml@main
```

The calling repo needs a `Dockerfile` at its root and nothing else.
