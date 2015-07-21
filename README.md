# test

Testing some git merging and rebasing stuff. This is fun!

Now we're doing some branch work. Branches that merge with no-ff look ugly.

Now we commit with ff (fast-forward) enabled; but what about conflicts? We resolve them as usual with merges.

Another merge with no conflicts! If you are using `git rebase` with your development branches, this is what your git commit history should look like: clean. A straight line. Immaculate.

# See it yourself

To review the git history, run the following in your console:

    git log --oneline --graph

You may omit the `--oneline` option for slightly more verbosity. If you have a favorite git client, you may use that instead, but I use the command-line tools so I have no idea how any of the GUI clients work.

Non-fast-forward merges were made using `git merge --no-ff` and fast-forward merges were made using `git merge --ff`.

# GitHub and merges

Unfortunately GitHub forces users to have non-fast-forward merges when using their Pull Request system. For this reason I suggest that projects wishing to have a simpler and cleaner commit history use local git commands to perform the merge and then use GitHub only to pull and push changes.

The flow would look something like:

1. Create Pull Request or open an Issue.
2. Create a custom branch to perform work.
3. Push work branch and submit it for code review.
4. The reviewer that will ultimately accept the changes will fetch the branch, run `git merge --ff`, and push the result upstream. If the merge throws conflicts, the changes should be discarded and the work branch should be rebased to eliminate conflicts.
