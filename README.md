# HubSpot Project Upload Action

Automatically upload a HubSpot Project to your account 🚀

## Usage
In your GitHub repo, create two new [secrets](https://docs.github.com/en/free-pro-team@latest/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository) for:
- `HUBSPOT_ACCOUNT_ID` - This is your HubSpot account ID
- `HUBSPOT_PERSONAL_ACCESS_KEY` - Your [personal access key](https://developers.hubspot.com/docs/cms/personal-cms-access-key)

This guide walks through setting up a new workflow file that automatically uploads new changes on your `main` branch to your HubSpot account. If you're adding a deployment step to an existing workflow, you can [skip ahead](#integrating-into-an-existing-workflow).

1. In your project, create a GitHub Action workflow file at `.github/workflows/main.yml`
2. Copy the following example workflow into your `main.yml` file.
```yaml
on:
  push:
    branches:
    - main
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2.3.3
      - name: HubSpot Project Upload Action
        uses: HubSpot/hubspot-project-upload-action@v1.3
        with:
          account_id: ${{ secrets.hubspot_account_id }}
          personal_access_key: ${{ secrets.hubspot_personal_access_key }}
```
4. Commit and merge your changes

*Note:* Do not change the `account_id` or `personal_access_key` values in your workflow. Auth related values should only be stored as GitHub secrets.

### Secrets
- `HUBSPOT_ACCOUNT_ID` - Target account id
- `HUBSPOT_PERSONAL_ACCESS_KEY` - Authentication key
