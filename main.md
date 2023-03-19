# Merge Repos Using Local Repo Remotes

Basic merge of two repos. If you want to merge more than two, choose the primary destination repo and keep merging the others one at a time.

For the following instructions, all repos are local. There is no issues if they are also remote on GitHub but must be cloned locally for these particular instructions to work. If you want to merge GitHub remotes rather than local, use [these instructions](https://github.com/pablisch/merge-repositories/blob/main/merge-using-github-remotes.md).

The following assumes https as cloning commmand. SSH may work too but I have not tested that.

```bash
git remote -v # will show remotes, fetch and push (optional step)
git remote add <custom-remote-name> <file-path><repo-name> # this is the same as the HTTPS cloning code
git remote -v # should now show additional remotes, fetch and push (optional step)

git fetch <custom-remote-name> # fetched but not yet accessible
# This will return infomation you will need for the merge, e.g.
# * [new branch]   <default-branch>   -> <custom-remote-name>/<default-branch>

# to merge the new remote - assuming that it has an unrelated history to the original remote
git merge <custom-remote-name> --allow-unrelated-histories
```

There may be conflicts that need to be managed before a merge can take place. The easiest way to deal with these is in VSCode. Clicking on the files with conflicts will lead to options to accept or resolve in the Merge Editor.

```bash
git remote remove <custom-remote-name>
```
