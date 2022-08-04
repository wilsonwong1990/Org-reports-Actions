# Org-reports-Actions


### Permissions-Report Action

To use this copy the `actions.yaml` to your `.github/workflow` directory in your repository. This Actions workflow will not worked called.

The Action requires a Personal Access Token that has organization access along with `repo` and `org:read` scopes. The Action will then use the REST API to gather a list of organization repositories, for each repository get the list of members, and then return the permissions for each user. This then gets converted into a csv that is then placed in the /Permissions-report directory of the repository. 

Do note there is no throttling for API requests so for large organizations, it may hit rate limit issues.
