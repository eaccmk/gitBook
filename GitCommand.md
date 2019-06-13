> Git Squash

| Ref: https://stackoverflow.com/questions/5189560/squash-my-last-x-commits-together-using-git/21890252#21890252 |

Add a global "squash" alias from bash: (or Git Bash on Windows)
`git config --global alias.squash '!f(){ git reset --soft HEAD~${1} && git commit --edit -m"$(git log --format=%B --reverse HEAD..HEAD@{1})"; };f'`

... or using Windows' Command Prompt:
`git config --global alias.squash "!f(){ git reset --soft HEAD~${1} && git commit --edit -m\"$(git log --format=%B --reverse HEAD..HEAD@{1})\"; };f"`

Your ~/.gitconfig should now contain this alias:

**[alias]**
    `squash = "!f(){ git reset --soft HEAD~${1} && git commit --edit -m\"$(git log --format=%B --reverse HEAD..HEAD@{1})\"; };f"`

Usage:

`git squash N`

... Which automatically squashes together the last N commits, inclusive.

Note: The resultant commit message is a combination of all the squashed commits, in order. If you are unhappy with that, you can always git commit --amend to modify it manually. (Or, edit the alias to match your tastes.)