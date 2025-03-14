# Update-nvmrc-action

Composite Github workflow for updating `.nvmrc` file.

## Prerequisites
To start using this action, you need to grant GitHub Actions permission to create pull requests. You can do this by enabling the option "Allow GitHub Actions to create and approve pull requests" in your GitHub organization settings (Settings → Actions → General).

## Inputs

### `use-only-lts`

Use LTS version of Node.js. Default true.

### `github-token`

**Required** Github token for creating a pull request with latest version (similar to dependabot)

## Example usage

```yaml
name: Update .nvmrc to latest LTS

on:
  schedule:
    - cron: '0 0 * * 1' # runs every Monday at 0:00 

  workflow_dispatch:
    
permissions:
  contents: write
  pull-requests: write

jobs:
  update-nvmrc:
    runs-on: ubuntu-latest
    timeout-minutes: 5
    steps:
      - uses: codemask-labs/update-nvmrc-action@v1.3.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```
