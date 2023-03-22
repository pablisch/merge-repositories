# Merge Repos Using GitHub Remotes

Basic merge of two repos. If you want to merge more than two, choose the primary destination repo and keep merging the others one at a time.

The following instructions are for using GitHub remotes but the primary repo that others are bing merged into must still be local. Clone the primary repo locally if it is not already local. If you wish to use local remotes instead, follow [these instructions](https://github.com/pablisch/merge-repositories/blob/main/merge_using_local_remotes.md). Neither is any harder or easier than the other.

NOTE: the only difference in using local remotes is the target when adding the new remote.

The following assumes https as cloning commmand. SSH may work too but I have not tested that.

```bash
git remote -v # will show remotes, fetch and push (optional step)
git remote add <custom-remote-name> <second-repo-url>.git # this is the same as the HTTPS cloning code
git remote -v # should now show additional remotes, fetch and push (optional step)

git fetch <custom-remote-name> # fetched but not yet accessible
# This will return infomation you will need for the merge, e.g.
# * [new branch]   <default-branch>   -> <custom-remote-name>/<default-branch>

# to merge the new remote - assuming that it has an unrelated history to the original remote
git merge <custom-remote-name>/<default-branch> --allow-unrelated-histories
```

There may be conflicts that need to be managed before a merge can take place. The easiest way to deal with these is in VSCode. Clicking on the files with conflicts will lead to options to accept or resolve in the Merge Editor.

```bash
git remote remove <custom-remote-name>
```
