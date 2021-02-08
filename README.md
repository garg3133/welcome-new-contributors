# Welcome New Contributors
Use this action to welcome the new contributors into your community. This action posts a welcome message whenever a new contributor opens his/her first issue or PR in your repository.

Additionally, you can also create your own bot account and use it to post the welcome messages instead of using the default `github-actions` bot.

This action is inspired by [first-interaction](https://github.com/actions/first-interaction). Thanks to all the contributors of first-interaction.

# Usage

Sample usage for using the default `github-actions` bot to post the welcome messages:

```
name: 'Welcome New Contributors'

on:
  issues:
    types: [opened]
  pull_request_target:
    types: [opened]

jobs:
  welcome-new-contributor:
    runs-on: ubuntu-latest
    steps:
      - name: 'Greet the contributor'
        uses: garg3133/welcome-new-contributors@v1
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          issue-message: 'Hello there, thanks for opening your first issue. We welcome you to the community!'
          pr-message: 'Hello there, thanks for opening your first Pull Request. Someone will review it soon.'
```
