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

# The graph

For those too lazy, here is what the final history should look like, with some edits to make the commit intentions more obvious.

    * 4616328 Final touches
    * d575188 Merge with ff again - no conflicts
    *   048a38b Merge commit for --ff with conflicts
    |\  
    | * bcfafbe This branch has a conflict with master
    * | c7d2cb5 Some change made to master intended to cause conflict
    |/  
    * 6b23bfe Merged with --ff and no conflicts; looks like a direct commit
    *   9a0aab8 Merge commit generated due to --no-ff; no conflicts
    |\  
    | * 1db7988 Another commit with no conflicts
    |/  
    *   ecf0f16 Merge commit generated due to --no-ff; no conflicts
    |\  
    | * cdd220f A branch that contains no conflicting merges
    |/  
    * 07995d3 Second direct commit
    * d9b78ee Direct commit - no merging, just commit and push
    * 2c00621 Initial commit

# GitHub and merges

Unfortunately GitHub forces users to have non-fast-forward merges when using their Pull Request system. For this reason I suggest that projects wishing to have a simpler and cleaner commit history use local git commands to perform the merge and then use GitHub only to pull and push changes.

The flow would look something like:

1. Create Pull Request or open an Issue.
2. Create a custom branch to perform work.
3. Push work branch and submit it for code review.
4. The reviewer that will ultimately accept the changes will fetch the branch, run `git merge --ff`, and push the result upstream. If the merge throws conflicts, the changes should be discarded and the work branch should be rebased to eliminate conflicts.
