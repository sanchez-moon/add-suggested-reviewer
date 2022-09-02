# Add suggested reviewer

This repo inspirited by https://github.com/molleer/blame-alert

### Usage

```yml
name: CI
on:
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
        with:
          ref: ${{ github.base_ref }}
          fetch-depth: 0
      - name: Blame Alert
        uses: molleer/blame-alert@master
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Example

User1 has made a new PR to a repo which is using `molleer/blame-alert`. He/she has deleted a few lines of code which User2 had written. When the PR is created, this comment is added to the PR by `molleer/blame-alert`.

![example](https://raw.githubusercontent.com/molleer/blame-alert/master/example.png)

If User1 only changes the code which he/she has added since before, `molleer/blame-alert` will not add an alert comment.
