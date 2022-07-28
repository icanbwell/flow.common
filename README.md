# Common Github Workflows for b.Well

This repository houses common Github workflows for b.Well.

To use a workflow from here, please configure your workflow like this:

```yaml
jobs:
  autotag:
    uses: icanbwell/flow.common/.github/workflows/auto-release.yaml
    secrets: inherit
  helm-publish:
    needs: autotag
    uses: icanbwell/flow.common/.github/workflows/helm-publish.yaml
    secrets: inherit
    with:
      version: ${{ needs.autotag.outputs.tag }}
```