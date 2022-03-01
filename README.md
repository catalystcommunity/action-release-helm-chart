<!-- start title -->

# GitHub Action:Release helm chart

<!-- end title -->
<!-- start description -->

Releases helm charts using semantic-release with the @catalystsquad/release-config-helm release config. This action uses main and alpha branches and releases. This action deletes the alpha branch and re-creates it from main after a release from main

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: catalystsquad/action-release-helm-chart@undefined
  with:
    # github token to use for the release, if you want this to trigger other workflows
    # such as flows on release created, pass in a PAT
    # Default: ${{ github.token }}
    token: ""

    # If true, this action will disable the `include administrators` setting in branch
    # protection for this branch, and re-enable it after release. Re-enabling is run
    # using always()
    # Default: false
    toggle-admins: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**           | **Description**                                                                                                                                                                |      **Default**      | **Required** |
| :------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------: | :----------: |
| **`token`**         | github token to use for the release, if you want this to trigger other workflows such as flows on release created, pass in a PAT                                               | `${{ github.token }}` |  **false**   |
| **`toggle-admins`** | If true, this action will disable the `include administrators` setting in branch protection for this branch, and re-enable it after release. Re-enabling is run using always() |                       |  **false**   |

<!-- end inputs -->
<!-- start outputs -->

| **Output**      | **Description** | **Default** | **Required** |
| :-------------- | :-------------- | ----------- | ------------ |
| `random-number` | Random number   |             |              |

<!-- end outputs -->
<!-- start examples -->

### Example usage

```yaml
name: Release
on:
  pull_request:
    types:
      - closed
    branches:
      - main
      - alpha
    paths:
      - "chart/**"
jobs:
  release:
    name: Release chart
    if: github.event.pull_request.merged == true
    runs-on: ubuntu-latest
    steps:
      - uses: catalystsquad/action-release-helm-chart@v1
        with:
          token: ${{ secrets.AUTOMATION_PAT }}
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
