# Git Stash Guide

## Overview
This guide provides an overview of Git stash operations and how to use them effectively.

---

## What is Git Stash?


The git stash command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy.


---

## Temporarily Saving Uncommitted Changes

```
git stash
```
- This saves both staged and unstaged changes.
- Your working directory is now clean, as if you never made changes.

   

---

## Listing and Describing Stashed Changes

```
git stash list
```
This shows a summary of all stashes with their descriptions.


---

## Restoring Stashed Changes

**1. Apply the Most Recent Stash (Keep Stash)**
```
git stash apply
```
- This reapplies the latest stash, but does not remove it from the stash list.
- If a merge conflict occurs, Git will ask you to resolve it before proceeding.

**2. Apply & Remove the Most Recent Stash**

```
git stash pop
```
This restores the latest stash and removes it permenantly from the stash list.



---

## Applying and Removing a Specific Stash

```
git stash apply <stash_name>
```
Use this if you want to use a specific stash, not the latest one.

---

## Dropping or Clearing Stashes

**1. Drop a Specific Stash**

  1.1 Get Stash List
  ```
  git stash list
  ```
  This will show all stashes with their details

  1.2. Drop stash
  ```
  git stash drop <stash_name>
  ```
**2. Clear All Stashes**

 ```
 git stash clear
 ```

⚠️ Warning: This action is irreversible! Make sure you no longer need any stashed changes before running this command.
---

## Git Stash Pop vs. Git Stash Apply

- git stash pop: Applies the latest stashed changes and removes them from the stash list.
- git stash apply: Applies the latest stashed changes but keeps them in the stash list for future use.

 ### Usage
 - Use git stash apply if you want to keep the stash for future use.
 - Use git stash pop if you don’t need the stash anymore.

---

## Purpose of Git Stash Save with a Message
The command git stash save "message" allows you to stash your changes with a custom message, making it easier to identify different stashes later. 

```
git stash push -m "Write your message here"
```

Viewing the Stashes:
```
git stash list
```

Example output:

```
stash@{0}: On main: Fixing Issue 1
stash@{1}: On main: Fixing issue 2
```

---

## Stashing Changes for Specific Files


```
git stash push -m "Stashing only this file's changes" -- <file_name>
```

- This command stashes only this file's changes, leaving the other files unstashed.
- You can later restore the stash using git stash apply or git stash pop.

---

## Checking Affected Files in a Stash

```
git stash show <stash_name>
```
This displays a one-line summary of the files that were modified in this stash.

Example Output:

```
 index.js  | 5 +
 style.css | 3 -
```
