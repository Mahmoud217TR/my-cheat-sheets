# Stashing Files

**Table of Contents:**
* [Stashing](#stashing)
* [Stash Lists](#stash-lists)
* [Getting Files](#getting-files)
* [Showing stash contents](#showing-stash-contents)
* [Deleting a stsh](#deleting-a-stash)


## Stashing

To Stash a file:
    - Add the file `git add <file>`.
    - Stash it `git stash`.

To Stash with a message `git stash save "message"`.


## Stash Lists

To Display stashes `git stash list`.


## Getting files

- To get a stash use `git apply @stash{id}`.

- To get a stash and remove it use `git pop @stash{id}`.


## Showing stash contents

To show stash contents `git stash show stash@{id}`.


## Deleting a stash

To Delete a stash `git stash drop stash@{id}`.