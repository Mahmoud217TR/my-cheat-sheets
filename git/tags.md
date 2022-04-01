# Tagging

**Table of Contents:**
* [Show Tags](#show-tags)
* [Create Tags](#create-tags)
* [Delete Tags](#delete-tags)


## Show Tags

To show tags use `git tag`.


## Create tags

- To create light weight tag `git tag <tag>`, you need to push it to remote repo `git push origin <branch>`.

- To create annotated tag `git tag -a <tag> [-m "message"]`.


## Delete Tags

- To delete tag `git tag -d <tag>`, delete it from remote repo `git push origin --delete <tag>`.