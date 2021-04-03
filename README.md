# Delete old pull request artifacts (GitHub Action)

_GitHub Action to delete all workflow artifacts for a branch_

## Motivation

Artifacts generated by pull-requests can quickly use all the storage you paid for.
Usually, when the PR is merged or closed, artifacts belonging to that pull-request are no longer needed.
To delete them, use this GitHub Action.

## Usage

```yaml
name: PR cleanup

on:
  pull_request:
    types: [closed]

jobs:
  delete_pr_artifacts:
    runs-on: ubuntu-latest
    steps:
      - uses: stefanluptak/delete-old-pr-artifacts@v0.0.1
        with:
          workflow_filename: ci.yaml
```

## Parameters

| Parameter | Description | Required | Default |
| - | - | - | - |
| `workflow_filename` | Filename of the workflow that generated artifacts you want to delete  | ✅ |  |
| `github_token` | GitHub token used to authenticate you GitHub API calls | ❌ | `${{ secrets.GITHUB_TOKEN }}` |
| `github_repo` | GitHub repository you want to delete the artifact in | ❌ | `${{ github.repository }}` |
| `git_branch` | Git branch of the pull request | ❌ | `${{ github.head_ref }}` |
| `debug` | Whether you want to see some debugging output. | ❌ | `false` |

## Notes

This is my first GitHub Action. Feel free to contribute, ask or give me advice on how to improve it. Thanks. :-)