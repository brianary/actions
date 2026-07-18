Reusable actions
================

Actions for repositories using some specific conventions.

🩺 Continuous integration
-------------------------

```yaml
name: 🩺 Continuous integration ⏩

on:
  push:
    branches: [main]
    paths: ['scripts/**','src/**','test/**']
  pull_request:
    types: [opened, reopened]
    branches: [main]
    paths: ['scripts/**','src/**','test/**']
  workflow_dispatch: {}

permissions:
  contents: read
  security-events: write
  actions: read

jobs:
  call-workflow:
    uses: brianary/actions/.github/workflows/continuous-integration.yml@main
```

📦 Publish module to PowerShell Gallery
---------------------------------------

```yaml
name: 📦 Publish module to PowerShell Gallery ⏩

on:
  push:
    tags:
      - v[0-9]*

permissions:
  contents: read
  security-events: write
  actions: read

jobs:
  call-workflow:
    uses: brianary/actions/.github/workflows/powershell-gallery-publish.yml@main
    with:
        version: ${{ github.ref }}
```
