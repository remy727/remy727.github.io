---
layout: post
title: "Change the commit author for a single commit"
date:   2023-06-05 13:00:00 -0400
categories: Git
comments: true
---

In this blog post, you will learn how to change the commit author for a single commit in Git. This can be useful if you accidentally committed with the wrong author information or if you need to update the author for any other reason.

## Step 1: Identify the commit

First, you need to identify the commit for which you want to change the author. You can do this by using the git log command to view the commit history. Find the commit hash (a unique identifier) of the commit you want to modify.

```bash
git log --pretty=oneline
```

## Step 2: Modify the commit author

Once you have identified the commit hash, you can change the author information using the `git commit --amend` command. Replace `<commit-hash>` with the hash of the commit you want to modify, and replace **Author Name** and **email@address.com** with the new author's name and email address.

```bash
git rebase -i <commit-hash>^
```

In the text editor that opens, replace the word pick with edit for the commit you want to modify, then save and close the editor.

Now, amend the commit with the new author information:

```bash
git commit --amend --author="Author Name <email@address.com>"
```

## Step 3: Continue the rebase

After changing the author information, continue the rebase process:

```bash
git rebase --continue
```

This will apply any remaining commits on top of the modified commit.

## Step 4: Push the new history

Finally, push the new history to the remote repository. Note that this will overwrite the remote history, so use this command with caution. If you are collaborating with others, make sure to inform them of the change.

```bash
git push --force-with-lease
```
And that's it! You have successfully changed the commit author for a single commit in Git 