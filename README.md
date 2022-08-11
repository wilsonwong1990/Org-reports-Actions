# Org-reports-Actions


### Permissions-Report Action

Still a work in progress at this time.

The Action requires a Personal Access Token that has organization access along with `repo` and `org:read` scopes. The Action will then use the REST API to gather a list of organization repositories, for each repository get the list of members, and then return the permissions for each user. This then gets converted into a csv that is then placed in the /Permissions-report directory of the repository. 

Do note there is no throttling for API requests so for large organizations, it may hit rate limit issues.

#### Calling the workflow

Set up a workflow in your own repository like this:

```
# Actions workflow that checks an org/user's repos and returns a csv of all the users along with repo permissions

name: Permissions Report caller

# Controls when the workflow will run
on:
  # Triggers at a set time
  schedule:
  - cron: "0 2 * * 1-5"

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

jobs:
  call-workflow-passing-data:
    uses: wilsonwong1990/Org-reports-Actions/.github/workflows/action-reusable.yml@main
    secrets:
      PAT: ${{ secrets.PAT }}
```

Feel free to change the cron job or allowing for `workflow_dispatch`.
