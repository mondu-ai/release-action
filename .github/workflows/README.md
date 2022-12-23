### RELEASE ACTION

CI reusable workflow for github actions.

Existing version tag should be SemVer(major.minor.patch) with v prefix. F.E. v0.0.1

Usage


```yml
jobs:
  # Job name
  release:
    name: auto_release
    # Should work only if Pull Request was merged
    if: github.event.pull_request.merged == true
    # Importing from repository, can only import from organization repositories
    uses: mondu-ai/release-action/.github/workflows/release-update.yml@master
    with:
      # Only required argument, need to pass script which will create assets, last line in required, specify names of files that should be pushed to assets F.E. stuff.zip entry.zip new.zip
      asset_creation_script: |
        zip -r entry.zip entrypoint.sh
        zip -r stuff.zip some_stuff.sh
        zip -r new.zip new_file.sh
        echo "FILES="stuff.zip entry.zip new.zip"" >> $GITHUB_ENV

```

You can access tag value in script from env under NEW_TAG variable
