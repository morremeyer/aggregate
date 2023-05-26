# aggregate

## Add repo
To add a new repo go to the 'Actions' tab in GitHub and select 'Add repo' action.
For input use a conda-forge feedstock. Separate multiple feedstocks by comma.

Example: `7za-feedstock,7zip-feedstock`

The action will look up the feedstock and append any dependencies it has to the list of feedstocks. Any feedstocks
that have already been forked into anaconda-community will be removed from the list. The remaining feedstocks will
be forked into anaconda-community and a PR is created that adds these forked repos to manifest.yaml.

## Remove repo
To remove a repo go to the 'Actions' tab in GitHub and select 'Remove repo' action.
For input use the repo name. 

Example: `7za-feedstock`

This will remove the forked repo from anaconda-community and create a PR that removes feedstock from manifest.yaml.

## Build
Whenever a PR is opened or merged where manifest.yaml has been updated the file will be parsed and additions to it will
trigger a new build.

## Updates
On a schedule defined in update-repo.yml all forks will be synced with upstream and a PR will be created with any changes to manifest.yaml

## Integration test

To run the integration test locally, 
- install [Act](https://github.com/nektos/act)
- configure act to use a runner 
- create a github personal access token and put in a `.env` file

Run update-manifest job:
```
act -j update-manifest -W .github/workflows/integration-test.yml -s GITHUB_TOKEN
```

## Pinned packages
We maintain a list of pinned packages in `conda_build_config.yaml` that we sync from AnacondaRecipes and conda-forge/conda-forge-pinning-feedstock. 
Feedstocks for packages in AnacondaRecipes conda_build_config should not be included in community repo.
To support additional pinnings for community repo we have a file `conda_build_config_community.yaml` that will be merged with `conda_build_config.yaml` when the `sync-pinnings` workflow is run