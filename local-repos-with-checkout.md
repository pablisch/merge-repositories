# Merge Repos Using Local Repo Remotes
## Includes checkout to view repos in terminal before merge

This is a more complex option to the [main.md](https://github.com/pablisch/merge-repositories/blob/main/main.md) version which includes checking out to a new remote branch to view files. As a git novice, I recommend comparing folders and files in Finder or VSCode rather than using this method.

For the following instructions, all repos are local. There is no issues if they are also remote on GitHub but must be cloned locally for these particular instructions to work. If you want to merge GitHub remotes rather than local, see **\*\*\*** link to follow **\*\***.

The following assumes https as cloning commmand. SSH may work too but I have not tested that.

NOTE: I have always merged repositories as shown in [main.md](https://github.com/pablisch/merge-repositories/blob/main/main.md). Those instruction were adapted from these but I have not tested these myself, nor recommend them.

```bash
git remote -v # will show remotes, fetch and push (optional step)
git remote add <custom-remote-name> <second-repo-url>.git # this is the same as the HTTPS cloning code
git remote -v # should now show additional remotes, fetch and push (optional step)

git fetch <custom-remote-name> # fetched but not yet accessible
# This will return infomation you will need for the merge, e.g.
# * [new branch]   <default-branch>   -> <custom-remote-name>/<default-branch>

git checkout -b <new-branch-name> <custom-remote-name>/main # inspect files and check that they are what you want to merge with the primary repo
```
NOTE: the -b is the flag for a new branch
```bash
git checkout main # to return to the main branch

# to merge the new remote - assuming that it has an unrelated history to the original remote
git merge <new-branch-name>/main --allow-unrelated-histories  
```

There may be conflicts that need to be managed before a merge can take place. The easiest way to deal with these is in VSCode. Clicking on the files with conflicts will lead to options to accept or resolve in the Merge Editor.

```bash
git remote remove <custom-remote-name>
```
