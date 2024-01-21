# release-exists-action
Action for checking if release exists in repository

### usage

```
name: test if release exists

on:
  workflow_dispatch:
    inputs:
      releasename:
        description: "release name"
        required: true

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out code
        uses: actions/checkout@v3
      - name: test if release exists
        uses: oskarirauta/release-exists-action@v2
        with:
          token: ${{ github.token }}
          release: ${{ inputs.releasename }}
      - name: show result
        shell: bash
        run: |
          echo "release ${{ inputs.releasename }} exists: ${{ env.release_exists }}"
```
