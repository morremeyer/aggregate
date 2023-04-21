# aggregate

## Add repo
To add a new repo go to the 'Actions' tab in GitHub and select 'Add repo' action.
For input use a conda-forge feedstock. Separate multiple feedstocks by comma

Example: 7za-feedstock,7zip-feedstock

This will fork the repo into anaconda-community org and create a PR that adds this feedstock to manifest

## Update repo
To update a repo go to the 'Actions' tab in GitHub and select 'Update repo' action.
For input use the repo name. 

Example: 7za-feedstock

This will sync the already forked repo in anaconda-community and create a PR that updates the hash in manifest

## Remove repo
To remove a repo go to the 'Actions' tab in GitHub and select 'Remove repo' action.
For input use the repo name. 

Example: 7za-feedstock

This will remove the forked repo from anaconda-community and create a PR that updates manifest