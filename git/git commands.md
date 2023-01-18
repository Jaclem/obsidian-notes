`git clone git@github.com:Jaclem/tic-tac-toe.git`
git clone will allow you to clone an existing repository and place that folder in whichever folder you are currently in

`git add .`
Adds all file changes to the staging area of git

`git commit -m "Your Message"`
Adds a commit message

`git push`
Pushes your changes to your repository

`git pull <link>`
Pulls all changes that were made to the repo so that your local files can be up to date

`git add`
`git commit --amend`
git commit --amend allows us to replace the last commit with an entirely new one. 

`git rebase -i`
A command which allows us to interactively stop after each commit we’re trying to modify, and then make whatever changes we wish.

`git rebase -i HEAD~2`
For example, the above command allows us to edit the last two commits.

```bash
pick 3f72844 create second file
pick e89149f Create fourth file

 Rebase 35e9bcb..e89149f onto 35e9bcb (2 commands)

 Commands:
 p, pick <commit> = use commit
 r, reword <commit> = use commit, but edit the commit message
 e, edit <commit> = use commit, but stop for amending
 s, squash <commit> = use commit, but meld into previous commit
 f, fixup [-C | -c] <commit> = like "squash" but keep only the previous
                    commit's log message, unless -C is used, in which case
                    keep only this commit's message; -c is same as -C but
                    opens the editor
 x, exec <command> = run command (the rest of the line) using shell
 b, break = stop here (continue rebase later with 'git rebase --continue')
 d, drop <commit> = remove commit
 l, label <label> = label current HEAD with a name
 t, reset <label> = reset HEAD to a label
 m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
         create a merge commit using the original merge commits
         message (or the oneline, if no original merge commit was
         specified); use -c <commit> to reword the commit message
 u, update-ref <ref> = track a placeholder for the <ref> to be updated
                       to this position in the new commits. The <ref> is
                       updated at the end of the rebase

 These lines can be re-ordered; they are executed from top to bottom.

 If you remove a line here THAT COMMIT WILL BE LOST.

 However, if you remove everything, the rebase will be aborted.
```

When satisfied with the changes made we can amend the commit now `git commit --amend` and `git rebase --continue` 

`Squash`ing makes it easier for others to understand the history of your project. What often happens when a feature is merged, is we end up with some visually complex logs of all the changes a feature branch had on a main branch.

`git push origin <branch-name>` 
When we push origin we are pushing a different branch indicated by branch name to our master file (our default main / master file). So if there is a diverging branch that needs to be merged we can do it like this.
From there we would go to `github.com` and click =="Merge pull request"== 

