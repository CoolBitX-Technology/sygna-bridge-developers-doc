# Automatically Sync API Specification with GitHub

With ![GitHub Actions](https://github.com/features/actions) it's super easy to automatically sync your Swagger or OpenAPI file whenever changes occur in your GitHub repo!

Just copy and paste the following into `.github/workflows/readme-github-sync.yml.` You only need to modify three of the parameters in the GitHub Action--the path to your API file, your ReadMe project's API key, and the ![ReadMe version](https://docs.readme.com/guides/docs/versions) you want to upload to. The other two parameters, repo-token and readme-api-id, should just be copied from these docs!

Once that is done you should be good to go! Any subsequent commits to master will automatically start the sync process and sync your specified file to ReadMe.

```
name: Sync to ReadMe

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest
    
    steps:
    - uses: readmeio/github-readme-sync@1.0.1
      with:
        repo-token: '${{ secrets.GITHUB_TOKEN }}' # DON'T MODIFY--Allows us to get the contents of your spec file
        readme-api-id: 'awNKtL2U2c3a' # DON'T MODIFY--Autogenerated to match API Settings in ReadMe to synced file!
        api-file-path: 'PATH-TO-FILE.json' # path to API spec file
        readme-api-key: 'ReadMe API Key' # ReadMe API key 
        readme-api-version: 'README-VERSION' # ReadMe version to sync to
```
