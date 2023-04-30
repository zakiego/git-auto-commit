# Git Push Action

This GitHub Action pushes changes to a remote Git repository.

## Inputs

| Input            | Description                                    | Required |
| ---------------- | ---------------------------------------------- | -------- |
| `email`          | The email address of the Git user.             | Yes      |
| `username`       | The username of the Git user.                  | Yes      |
| `commit-message` | The commit message to use.                     | Yes      |
| `github-token`   | The GitHub access token for the repository.    | Yes      |
| `repository`     | The name of the repository to push changes to. | Yes      |
| `branch`         | The name of the branch to push changes to.     | Yes      |

## Example usage

```yaml
name: Push changes to Git repository

on:
  push:
    branches: [main]

jobs:
  push-to-git:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Push changes
        uses: zakiego/git-push-action@main
        with:
          USERNAME: "github-actions[bot]"
          EMAIL: "41898282+github-actions[bot]@users.noreply.github.com"
          commit-message: "Test auto push"
          BRANCH: ${{ github.ref_name }}
          REPOSITORY: ${{ github.repository }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

In the above example, the action runs when changes are pushed to the `main` branch. It first checks out the code and then runs the `zakiego/git-push-action` action to push the changes to the specified remote Git repository. Make sure to set the required input values for your specific use case.
