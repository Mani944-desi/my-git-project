******************************************************************************* REBASE & STASH ***************************************************************

ubuntu@ip-172-31-40-115:~/my-git-project$ # if temp-change.txt exists (from step 1)
git stash push -u -m "WIP: include untracked temp-change"
git stash list
Saved working directory and index state On feature-add-greet: WIP: include untracked temp-change
stash@{0}: On feature-add-greet: WIP: include untracked temp-change
stash@{1}: On feature-add-greet: WIP: tracked change
ubuntu@ip-172-31-40-115:~/my-git-project$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
ubuntu@ip-172-31-40-115:~/my-git-project$ git merge feature-1
Already up to date.
ubuntu@ip-172-31-40-115:~/my-git-project$ git checkout -b feature-rebase
echo "Rebase demo" > rebase.txt
git add rebase.txt
git commit -m "feat: rebase demo commit"
Switched to a new branch 'feature-rebase'
[feature-rebase 080f934] feat: rebase demo commit
 1 file changed, 1 insertion(+)
 create mode 100644 rebase.txt
ubuntu@ip-172-31-40-115:~/my-git-project$ git checkout main
echo "Main update" > main-update.txt
git add main-update.txt
git commit -m "chore: update main"
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
[main e26bc0e] chore: update main
 1 file changed, 1 insertion(+)
 create mode 100644 main-update.txt
ubuntu@ip-172-31-40-115:~/my-git-project$ git checkout feature-rebase
git rebase main
Switched to branch 'feature-rebase'
Successfully rebased and updated refs/heads/feature-rebase.
ubuntu@ip-172-31-40-115:~/my-git-project$ git stash list
stash@{0}: On feature-add-greet: WIP: include untracked temp-change
stash@{1}: On feature-add-greet: WIP: tracked change



************************************************************************* Git Log graph ********************************************************************
ubuntu@ip-172-31-40-115:~/my-git-project$ git log --graph
* commit b1b038883ac07aab9ec870f06bcc3f992d9ed072 (HEAD -> feature-add-greet, origin/main, origin/feature-add-greet, main, feature-conflict)
| Author: Manikant Singh <manikantsing12@gmail.com>
| Date:   Mon Nov 17 13:20:12 2025 +0000
|
|     feature: add conflict.txt
|
* commit c910a6de8ddc1b4e120a501d46d9800fa21a6b90
| Author: Manikant Singh <manikantsing12@gmail.com>
| Date:   Mon Nov 17 13:20:12 2025 +0000
|
|     main: add conflict.txt
|
*   commit 79a9be44c8e2c76733493b1a86e8374e46118bdb
|\  Merge: 5aa365e 8edf8ef
| | Author: Manikant Singh <manikantsing12@gmail.com>
| | Date:   Mon Nov 17 13:19:41 2025 +0000
| |
| |     merge: feature-add-greet into main
| |
| * commit 8edf8ef0b9381462ddbf92fcc267a1566c96cdc5
|/  Author: Manikant Singh <manikantsing12@gmail.com>
|   Date:   Mon Nov 17 13:19:07 2025 +0000
|
|       feature: use util.greet in hello.sh
|
* commit 5aa365eb630550e1e5390103a2c99793f0fd5126 (origin/feature-1, feature-1)
  Author: Manikant Singh <manikantsing12@gmail.com>
  Date:   Mon Nov 17 12:41:25 2025 +0000

      Initial commit: add hello.sh and util.sh

************************************************************************ Extra ***************************************************************************
ubuntu@ip-172-31-40-115:~/my-git-project$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.sh
        util.sh

nothing added to commit but untracked files present (use "git add" to track)
ubuntu@ip-172-31-40-115:~/my-git-project$


ubuntu@ip-172-31-40-115:~/my-git-project$ git commit -m "Initial commit: add hello.sh and util.sh"
[master (root-commit) 5aa365e] Initial commit: add hello.sh and util.sh
 2 files changed, 4 insertions(+)
 create mode 100755 hello.sh
 create mode 100755 util.sh
ubuntu@ip-172-31-40-115:~/my-git-project$

ubuntu@ip-172-31-40-115:~/my-git-project$ git commit -m "Initial commit: add hello.sh and util.sh"
[master (root-commit) 5aa365e] Initial commit: add hello.sh and util.sh
 2 files changed, 4 insertions(+)
 create mode 100755 hello.sh
 create mode 100755 util.sh
ubuntu@ip-172-31-40-115:~/my-git-project$ ^C
ubuntu@ip-172-31-40-115:~/my-git-project$
ubuntu@ip-172-31-40-115:~/my-git-project$ git log --oneline --decorate --graph -n 5
* 5aa365e (HEAD -> master) Initial commit: add hello.sh and util.sh
ubuntu@ip-172-31-40-115:~/my-git-project$




