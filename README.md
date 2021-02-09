# Welcome New Contributors
Use this action to welcome the new contributors into your community. This action posts a welcome message whenever a new contributor opens his/her first issue or PR in your repository.

Additionally, you can also create your own bot account and use it to post the welcome messages instead of using the default `github-actions` bot.

This action is inspired by [first-interaction](https://github.com/actions/first-interaction). Thanks to all the contributors of first-interaction.

# Usage

#### Sample usage while using the default `github-actions` bot to post the welcome messages:

(Create a new workflow file (`workflowName.yml`) in `.github/workflows` directory of your repository and add the following code, with required changes in `issue-message` and `pr-message`)

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
        uses: garg3133/welcome-new-contributors@v1.0
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          issue-message: 'Hello there, thanks for opening your first issue. We welcome you to the community!'
          pr-message: 'Hello there, thanks for opening your first Pull Request. Someone will review it soon.'
```


#### Sample usage while using your own bot to post the welcome messages:
* Create a new GitHub account to be used as the bot.
* Add that GitHub account as a collaborator on your repository (so that it has permissions to write on your repository).
* Go to `Settings > Developer settings > Personal access tokens` and create a new token for this action so that this action can use your bot account to comment on issue/PRs).
* Go to your repository in which you want to use this action, open `Settings > Secrets > New repository secret` and add `BOT_ACCESS_TOKEN` as name and the token you copied in the above step as value.
* Now, create a new workflow file (`workflowName.yml`) in `.github/workflows` directory of your repository and add the following code (with required changes in `issue-message` and `pr-message`)
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
        uses: garg3133/welcome-new-contributors@v1.0
        with:
          token: ${{ secrets.BOT_ACCESS_TOKEN }}
          is-oauth-token: true
          issue-message: 'Hello there, thanks for opening your first issue. We welcome you to the community!'
          pr-message: 'Hello there, thanks for opening your first Pull Request. Someone will review it soon.'
```

# License
The scripts and documentation in this project are released under the [MIT License](https://github.com/garg3133/welcome-new-contributors/blob/main/LICENSE)
