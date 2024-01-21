# release-exists-action
Action for checking if release exists in repository

### note
use v1 if release name is un-quoted, and v2 if quoted.
It's usually quoted if release is retrieved from outputs variable, and if from inputs, then not..

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
