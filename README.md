# github-pr-merges

## create a merge commit

Pull request using the option "create a merge commit". This is the standard git-flow.

## squash and merge

[Squash and merge your pull request commits](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges#squash-and-merge-your-pull-request-commits)

"Pull requests with squashed commits are merged using the fast-forward option."

According to the documentation, the following happens:
1. squash the source branche (feature/e) commits
2. apply `git checkout develop`, then `git merge --ff-only feature/e`

### merging feature branch on main - example 1

Before:

![before squash and merge](./squash_and_merge_feature_branch/squash_and_merge_feature_branch_avant_1.PNG?raw=true)

After:

![after squash and merge](./squash_and_merge_feature_branch/squash_and_merge_feature_branch_apres_1.PNG?raw=true)

Warning: [If you plan to continue work on the head branch of a pull request after the pull request is merged, we recommend you don't squash and merge the pull request.](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges#squashing-and-merging-a-long-running-branch)

### merging feature branch on main - example 2

Before:

![before squash and merge](./squash_and_merge_feature_branch/squash_and_merge_feature_branch_avant_2.PNG?raw=true)

After:

![after squash and merge](./squash_and_merge_feature_branch/squash_and_merge_feature_branch_apres_2.PNG?raw=true)

### merging release branch on main

Before:

![before squash and merge](./squash_and_merge_feature_branch/squash_and_merge_feature_branch_avant_3.PNG?raw=true)

After:

![after squash and merge](./squash_and_merge_feature_branch/squash_and_merge_feature_branch_apres_3.PNG?raw=true)

### merging tag on develop

... starting from the beginning

# "git-flow" without merge commits ?

![1](./full-squash-merge/1.PNG?raw=true)

...

![2](./full-squash-merge/2.PNG?raw=true)

...

![3](./full-squash-merge/3_merge_release_into_main.PNG?raw=true)

...

![4](./full-squash-merge/4.PNG?raw=true)

...

![5](./full-squash-merge/5.PNG?raw=true)

...

![6](./full-squash-merge/6_merge_main_into_develop.PNG?raw=true)

...

![7](./full-squash-merge/7.PNG?raw=true)

MAYBE the problem is the tag. The tag may prevent git from rewriting the main commit onto develop

# "git-flow", no tag, without merge commits ?

![1](./full-squash-merge-no-tag/1.PNG?raw=true)

...

![2](./full-squash-merge-no-tag/2.PNG?raw=true)

...

![3](./full-squash-merge-no-tag/3_merge_release_into_main.PNG?raw=true)

...

![4](./full-squash-merge-no-tag/4.PNG?raw=true)

...

![5](./full-squash-merge-no-tag/5_merge_main_into_develop.PNG?raw=true)

...

![6](./full-squash-merge-no-tag/6.PNG?raw=true)

Same problem.

# "git-flow" using different GitHub PR merge strategies


![1](./different-merges/1.PNG?raw=true)

...

![2](./different-merges/2.PNG?raw=true)

...

Then we merge the release branch onto main, using a PR + merge commit.

![3](./different-merges/3.PNG?raw=true)

...

![4](./different-merges/4.PNG?raw=true)

Then we merge the tag onto develop, using a local command!

```
git checkout develop
git merge --ff-only 0.1.0
git push
```

![5](./different-merges/5.PNG?raw=true)

...

![6](./different-merges/6.PNG?raw=true)
