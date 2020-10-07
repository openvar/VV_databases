# Instructions for populating this folder

This folder is for markdown files that will be used by the VariantValidator platform. It will include

- Instructions for the batch tools
- Other documentation we choose to add

## Creating your local version of the repository
Install git and create a git account

Clone the repository

```bash
$ git clone https://github.com/openvar/VV_databases.git
```

## Adding content
In your local repository create a new branch to work on.
*Note, use a novel branch name*

```bash
# Note: Do not use the branch namee "my_branch", this is an example
$ git branch my_branch
# Checkout the branch
$ git checkout my_branch
``` 

To add files, create the file in your local repository, edit the file then use:
```bash
# Only markdown files go in this folder and must have the file handle .md
$ git add something.md
```
You can also modify files then stage them for sending to GitHub using the same git add command

## Committing content and pushing to GitHub
Add all the files you want to send to GitHub.
***Add only the giles you want to commit to prevent issues and also prevent sending incomplete content***

```bash
# Commit
$ git commit -m "Some meaningful message about what you are sending or have done"
# Push
$ git push -u origin my_branch
```

***Note: when committing, if the works performed are in response to an issue, add a hashIssueNumber to the commit for
 example***

```bash
$ git commit -m "These changes are made in response to issue #101"
```

When you are done pushing, inform admin so that necessary changes to the software can be made
`admin@variantvalidator.org`