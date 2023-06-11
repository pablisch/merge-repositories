# Merge different repos that have no related history

If you prefer a more narrative, less GitHub approach, there is a [blog post](https://medium.com/p/68280a7bcee5 "Blog post version of this GitHub repository... kind of") version with this repo.

[merge_using_local_remotes.md](https://github.com/pablisch/merge-repositories/blob/main/merge_using_local_remotes.md) is the base instructions for merging repos but yo can also see all its content copied below, 'Merge Repos Using Local Repo Remotes'.

[merge-using-github-remotes.md](https://github.com/pablisch/merge-repositories/blob/main/merge-using-github-remotes.md) includes the small difference from [merge_using_local_remotes.md](https://github.com/pablisch/merge-repositories/blob/main/merge_using_local_remotes.md) that it uses GitHub remotes rather than local ones.

- If you have your repositories on your local machine and you are able to specify their filepaths, use [merge_using_local_remotes.md](https://github.com/pablisch/merge-repositories/blob/main/merge_using_local_remotes.md).
- If you prefer to work with the GitHub remote repositories or simply find it easier to find their cloning addresses than local filepaths then use [merge-using-github-remotes.md](https://github.com/pablisch/merge-repositories/blob/main/merge-using-github-remotes.md).

[local-repos-with-checkout](https://github.com/pablisch/merge-repositories/blob/main/local-repos-with-checkout.md) adds checkout onto a new branch of the remote and merge that instead. Please note that these were the oiginal instructions that I came across but I have not tested them myself.

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
git merge <custom-remote-name>/<default-branch> --allow-unrelated-histories
```
Example:
```bash
git remote -v # will show remotes, fetch and push (optional step)
git remote add rev2 /Users/pablojoyce/projects/makers/review2 # this is the same as the HTTPS cloning code
git remote -v # should now show additional remotes, fetch and push (optional step)

git fetch rev2 # fetched but not yet accessible
# This will return infomation you will need for the merge, e.g.
# * [new branch]   <default-branch>   -> <custom-remote-name>/<default-branch>

# to merge the new remote - assuming that it has an unrelated history to the original remote
git merge rev2/main --allow-unrelated-histories
```

There may be conflicts that need to be managed before a merge can take place. The easiest way to deal with these is in VSCode. Clicking on the files with conflicts will lead to options to accept or resolve in the Merge Editor.

```bash
git remote remove <custom-remote-name>
```
