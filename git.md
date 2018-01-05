# git cheatsheet

- `git config --global core.editor "vim"` - Change default editor to `vim`. This is used for things like `git commit` and `git rebase -i`.
- `git rebase -i HEAD~2` - This lets you edit the last two commits, including doing things like squashing/fixup where you can mush the work of two commits together keeping one commit message.
- `git push --force origin master` - Make a mistake in your commits that you've pushed to the remote repo, cleaned it up locally, and want to erase your mistakes? This is the way to overwrite whatever's on the `master` branch on the remote `origin` repository. **Use with caution!!**
- `git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"` - Make a nice color-coded and abbreviated git log available with the command `git lg`.

## References:

1. [Github's git cheat sheet](https://education.github.com/git-cheat-sheet-education.pdf)
2. [Github git reference](http://git.github.io/git-reference/)
3. [Atlassian git config reference](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config)
4. [A better git log](https://coderwall.com/p/euwpig/a-better-git-log)
