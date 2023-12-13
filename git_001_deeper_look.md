# Git Deeper Look

### Change code editor for git messaging

`$ git config --global core.editor "code --wait"`

<details>
<summary>What it does</summary>

To make a commit with Visual Studio Code as the text editor, just type `$ git commit`. After you hit `Enter` a new tab in VS Code will open for you to write your commit message. You may provide more details on multiple lines as part of your commit message. After typing your commit message, save it `Ctrl + S`  and close the tab.
</details>


## Ammend

If you forgot to add to staging `myFile.js` when you did your last commit, you can `add myFile.js` and then do:

`$ git commit --amend`

This will edit your last file to have `myFile.js` as well

> Only do to commits that have not been pushed anywhere!

## Rebase

Show the last two commits and later choose how to edit:

`$ git rebase -i HEAD~2`

You'll get something like

```
pick eacf39d Some commit message
pick 92ad0af Another commit message
```

`$ git rebase -i --root`

Rebases up to root

### Remove/Rearrange commits
You can remove from the list, or change the order of how they appear in the text editor to remove/reorder the commits (then save and close).

### Edit message

Change the `pick` word to be `edit` (save and close). Then do `$ git commit --amend`, it will open a file of the commit message for you to edit (save and close) and then do `$ git rebase --continue`

### Squash

Change the `pick` word to be `squash` (save and cose). Now it will get squashed with the upper commit.


