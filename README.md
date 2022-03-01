<!-- start title -->

# GitHub Action:Hello World

<!-- end title -->
<!-- start description -->

Greet someone

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: catalystsquad/action-composite-action-template@undefined
  with:
    # Who to greet
    # Default: World
    who-to-greet: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**          | **Description** | **Default** | **Required** |
| :----------------- | :-------------- | :---------: | :----------: |
| **`who-to-greet`** | Who to greet    |   `World`   |   **true**   |

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
      - 'chart/**'
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
