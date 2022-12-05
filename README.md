# Add suggested reviewer

This repo inspirited by https://github.com/molleer/blame-alert

### Usage

```yml
name: Add suggested reviewer

on:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3
        with:
          # Add GITHUB PERSONAL ACCESS TOKEN to repository secrets
          # @see https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token
          token: ${{ secrets.PAT_TOKEN }}
          submodules: recursive
          fetch-depth: 0
      - name: Add Suggested Reviewer
        uses: sanchez-moon/add-suggested-reviewer@master
        with:
          GITHUB_TOKEN: ${{ secrets.PAT_TOKEN }}
```

### Example

User1 has made a new PR to a repo which is using `molleer/blame-alert`. He/she has deleted a few lines of code which User2 had written. When the PR is created, this comment is added to the PR by `molleer/blame-alert`.

![example](https://raw.githubusercontent.com/molleer/blame-alert/master/example.png)

If User1 only changes the code which he/she has added since before, `molleer/blame-alert` will not add an alert comment.
