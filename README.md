# gha-get-changed-files
Composite GitHub action that produces lists of files modified between given commit hashes or references using GitHub API. Will return structured json result.

The action was inspired by https://github.com/lots0logs/gh-action-get-changed-files and it's forks but I wanted to develop this more compact and readable alternative.

Resulting structured json object has following properties:
- added: Array of files added
- modified: Array of files modified
- renamed: Dictionary of files renamed, old name as key and new name as value
- deleted: Array of files deleted
- simple_add: Array of all files that are either modified, added or renamed (new file name)
- simple_delete: Array of all files that are either deleted or renamed (old file name)

Requires the contents read permission to your workflow:

```yaml
permissions:
  contents: read
```

# usage

```yaml
  - uses: ikudjoi/gha-get-changed-files@main
    with:
      base: main
      head: 456abc
```