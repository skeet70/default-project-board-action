<p align="center">
  <a href="https://github.com/skeet70/default-project-board-action/actions"><img alt="javscript-action status" src="https://github.com/skeet70/default-project-board-action/workflows/test/badge.svg"></a>
</p>

# Default Project Board Action

Intended to be used to set a default board for all new issues to automatically be added to.

## Usage

You can now consume the action by referencing the v1 branch

```yaml
name: "Default Project"

on:
  issues:
    types:
      - opened

jobs:
  add_to_project:
    runs-on: ubuntu-latest
    steps:
      - uses: skeet70/default-project-board-action@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          repository: ${{ github.repository }}
          issue: ${{ github.event.issue.number }}
          project: 1
```

See the [actions tab](https://github.com/actions/javascript-action/actions) for runs of this action! :rocket:

## Package for distribution

GitHub Actions will run the entry point from the action.yml. Packaging assembles the code into one file that can be checked in to Git, enabling fast and reliable execution and preventing the need to check in node_modules.

Actions are run from GitHub repos. Packaging the action will create a packaged action in the dist folder.

Run package

```bash
npm run package
```

Since the packaged index.js is run from the dist folder.

```bash
git add dist
```
