# addFixVersion
This action updates fix versions on Jira issues when the corresponding commits are merged to master or release branches - (release-candidate/release version branch).

#### Secrets the action uses
The action needs github token and a set of Jira credentials.
GitHub token is automatically provided, see https://docs.github.com/en/actions/security-guides/automatic-token-authentication#about-the-github_token-secret.
The Jira credentials should be added to the repository secrets as `JIRA_EMAIL` and `JIRA_TOKEN`.

#### Environment variables the action uses
The secrets stated above should be passed into the action environment as `GITHUB_TOKEN`, `JIRA_EMAIL` and `JIRA_TOKEN`.

#### Example of how to use action in a workflow
```
jobs:
  add_fix_version_to_issue:
    runs-on: ubuntu-latest
    steps:
      - uses: academicmerit/github-actions/addFixVersion@main
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          JIRA_EMAIL: ${{ secrets.JIRA_EMAIL }}
          JIRA_TOKEN: ${{ secrets.JIRA_TOKEN }}
```

#### Development
To update action, modify the `index.js` file, re-compile and push changes to repository.
To compile, you can use the [@vercel/ncc](https://github.com/vercel/ncc) tool. After installing the tool, simply `cd` into the `addFixVersion` directory and run `ncc build index.js`. This will update the files in the `dist` folder.

