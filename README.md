# Git Exercises

This comprehensive exercise combines essential Git skills, from manipulating history to advanced branching strategies.

### Resources

Before starting this exercise, Go through **Branching Model** and **Contribution rules and git flow** resources. When attempting the challenges, Try to use what you read as much as you can.

- [Branching Model](https://classic-cobalt-104.notion.site/Branching-model-c1f8f9686eef4d3594a8c1ca4955d451)
- [Contribution rules and git flow](https://classic-cobalt-104.notion.site/Contribution-rules-and-git-flow-0505d789170f4c0a8b7b5d7b41df7bf5)

### Getting Started:

1. **Create a New Git Repository:**

   - Head over to GitHub and create a new repository. Clone this repository to your local machine.
   ```bash
   

2. **Initialize Your Environment:**

   - Open a terminal window and navigate to your cloned repository directory.
   - Run the following commands to create some dummy files and commit them:

   ```bash
   touch test{1..4}.md
   git add test1.md && git commit -m "chore: Create initial file"
   git add test2.md && git commit -m "chore: Create another file"
   git add test3.md && git commit -m "chore: Create third and fourth files"
   ```

## Challenges:

**Part 1: Refining Git History (10 Challenges)**

1. **Missing File Fix:**

   - Run `git status` and `git log` to assess the current state of your repository.
   - From the status you will see that you forgot to add `test4.md` in the last commit.

   **Challenge:** Recover from this error by staging/adding `test4.md` and amending the commit message with an appropriate description.
```bash
ISARO@DESKTOP-JAF8I5H MINGW64 
$ git status
On branch main
Your branch is ahead of 'origi
  (use "git push" to publish y

Changes not staged for commit:
  (use "git add <file>..." to 
  (use "git restore <file>..."
        modified:   README.md

Untracked files:
  (use "git add <file>..." to 
        test4.md

no changes added to commit (us

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git add README.md 

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git commit -m "modified READ
[main b9a5fd0] modified README
 1 file changed, 203 insertion

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git status
On branch main
Your branch is ahead of 'origi
  (use "git push" to publish y

Untracked files:
  (use "git add <file>..." to 
        test4.md

nothing added to commit but un

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git log
commit b9a5fd0f13e05f88be8bcd0
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:39:18 20

    modified README

commit 377b7371d7d8c738c021dab
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:31 20

    chore: Create third and fo

commit 9ae188e21432646af70c1e7
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:20 20

    chore: Create another file

commit 214ed6c4d949a38ed1a6239
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:20 20

    chore: Create initial file

commit 762e148809bdc4747e835d6
Author: Leslie Isaro <14401754
Date:   Mon May 20 12:41:37 20

    Initial commit

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git status
On branch main
Your branch is ahead of 'origi
  (use "git push" to publish y

Untracked files:
  (use "git add <file>..." to 
        test4.md

nothing added to commit but un
Created 4th file

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git add test4.md

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git commit -- amend --no-edi
error: pathspec 'amend' did no
error: pathspec '--no-edit' di

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git commit --amend --no-edit
[main 30355a1] modified README
 Date: Mon May 20 13:39:18 202
 2 files changed, 203 insertio
 create mode 100644 test4.md

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git commit --amend
[main f276595] Created 4th fil
 Date: Mon May 20 13:39:18 202
 2 files changed, 203 insertio
 create mode 100644 test4.md
 ```

2. **Editing Commit History:**

   - It's crucial to maintain accurate commit messages. Modify the message from "Create another file" to "Create second file".

   **Challenge:** Utilize interactive rebasing (`git rebase -i HEAD~2`) to edit the commit message and ensure clarity. learn more about git `rebase` [here](https://www.bryanbraun.com/2019/02/23/editing-a-commit-in-an-interactive-rebase/)
   
```
ISARO@DESKTOP-JAF8I5H MINGW64 
$ git rebase -i HEAD~2
[detached HEAD 53c4bbe] Create
 Date: Mon May 20 13:39:18 202
 2 files changed, 203 insertio
 create mode 100644 test4.md
Successfully rebased and updat

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git status
On branch main
Your branch is ahead of 'origi
  (use "git push" to publish y

nothing to commit, working tre

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git log
commit 53c4bbee35599061ff19ce6
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:39:18 20
pick 377b737 chore: Create thi
Created 4th file

    Create second file

commit 377b7371d7d8c738c021dab
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:31 20

    chore: Create third and fo
reword 9ae188e chore: Create s
chore: Create second file

commit 9ae188e21432646af70c1e7
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:20 20

    chore: Create another file


pick 214ed6c chore: Create ini
chore: create initial file
```

3. **Keeping History Tidy - Squashing Commits:**

   - Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.

   **Challenge:** Use interactive rebasing with the `squash` command to achieve this. learn more about `squash` [here](https://mattstauffer.com/blog/squashing-git-commits-with-interactive-rebase/)
```
ISARO@DESKTOP-JAF8I5H MINGW64 
$ git rebase -i HEAD~2
[detached HEAD 16c4455] Create
 Date: Mon May 20 13:39:18 202
 2 files changed, 203 insertio
 create mode 100644 test4.md
Successfully rebased and updat

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git rebase -i HEAD~3
[detached HEAD 92af64f] chore:
 Date: Mon May 20 13:38:20 202
 1 file changed, 0 insertions(
 create mode 100644 test2.md
Successfully rebased and updat

ISARO@DESKTOP-JAF8I5H MINGW64 
$ git rebase -i HEAD~4
[detached HEAD 6e13d5a] chore:
 Date: Mon May 20 13:38:20 202
 2 files changed, 0 insertions
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updat
```

4. **Splitting a Commit:**

   - Imagine "Create third and fourth files" describes too much at once. Separate them for better tracking with two different commit messages: "Create Third File" and "Create fourth file".

   **Challenge:** Leverage `git reset` to separate the files into individual commits with distinct messages. learn more about `splitting commits` [here](https://dev.to/timmouskhelichvili/how-to-split-a-git-commit-into-multiple-ones-3g6f)
```bash
ISARO@DESKTOP-JAF8I5H MINGW64 
$ git log
commit 2abf6fc437a90928bb272f3
Author: l-isaro <l.isaro@alust

    Created 4th file

commit dac17da95384b5610096e65
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:31 20

    chore: Create third and fo

commit 6e13d5a65e7bdc69c758429
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:20 20

    chore: create initial file


ISARO@DESKTOP-JAF8I5H MINGW64  (main)
$ git reset Head~1
Unstaged changes after reset:
M       README.md

ISARO@DESKTOP-JAF8I5H MINGW64  (main)
$ git log
commit dac17da95384b5610096e65in)
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:31 20

    chore: Create third and fo

commit 6e13d5a65e7bdc69c758429
Author: l-isaro <l.isaro@alust
Date:   Mon May 20 13:38:20 20

    chore: create initial file

    chore: Create initial file

    chore: Create second file

commit 762e148809bdc4747e835d6

ISARO@DESKTOP-JAF8I5H MINGW64  (main)
$ git reset Head~
Unstaged changes after reset:
M       README.md

ISARO@DESKTOP-JAF8I5H MINGW64  (main)
$ git add README.md

ISARO@DESKTOP-JAF8I5H MINGW64  (main)
$ git commit -m "added a READM
[main 50fd728] added a README
 1 file changed, 203 insertion

ISARO@DESKTOP-JAF8I5H MINGW64 Advance
d (main)

ISARO@DESKTOP-JAF8I5H MINGW64 tSARO@DESKTOP-JAF8I5H MINGW64 Advanced (main)
$ git add test3.md

ISARO@DESKTOP-JAF8I5H MINGW64 mGifile changed, 0 insertions(tAdvanced (main)
$ git add test3.md
ISARO@DESKTOP-JAF8I5H MINGW64 GyARO@DESKTOP-JAF8I5H MINGW64 mGitAdvanced (main)
$ git add test3.md

ISARO@DESKTOP-JAF8I5H MINGW64 entGitAdvanced (main)
s/TheGymGitAdvanced (main)
$ git add test3.md

ISARO@DESKTOP-JAF8I5H MINGW64 entit commit -m "Create Third 
ISARO@DESKTOP-JAF8I5H MINGW64 ocumt commit -m "Create Third ents/TheGymGitAdvanced (main)     n 4ec3ede] Create Third Fi
$ git add test3.md

ISARO@DESKTOP-JAF8I5H MINGW64 ocums(-)
ents/TheGymGitAdvanced (main)     
$ git commit -m "Create Third Documents/TheGymGitAdvanced (main)
$ git commit -m "Create Third 
File"
[main 4ec3ede] Create Third File
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md  

ISARO@DESKTOP-JAF8I5H MINGW64 
~/Documents/TheGymGitAdvanced (main)
$ git add test4.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git commit -m "Create fourth file"
[main 23c3ca4] Create fourth file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md
 ```
5. **Advanced Squashing:**

   - Let's explore more complex squashing. Can you combine the last two commits ("Create third file" and "Create fourth file") into a single commit named "Create third and fourth files"?

   **Challenge:** Utilize interactive rebasing with the `squash` command to achieve this advanced squash. **Check step 4**
```
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase Head~2
error: cannot rebase: You have unstaged changes.
error: Please commit or stash them.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 3 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git status
On branch main
Your branch and 'origin/main' have diverged,
and have 3 and 2 different commits each, respectively.
pick 23c3ca4 Create fourth file
  (use "git pull" if you want to integrate the remote branch with yours)

nothing to commit, working tree clean

pick 50fd728 added a README
Create third and fourth files
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase Head~2
Current branch main is up to date.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase Head~2
Current branch main is up to date.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase Head~1
Current branch main is up to date.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase -i Head~1
Successfully rebased and updated refs/heads/main.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase -i Head~3
[detached HEAD e1de255] Create third and fourth files
 Date: Mon May 20 16:33:06 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git log
commit e1de2554075b1ac298527fa23d2c343be7e0166a (HEAD -> main)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:33:06 2024 +0200

    Create third and fourth files

    Create Third File

    Create fourth file

commit 50fd728712c30d94cb7d27e072b1acf951db070a
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:29:12 2024 +0200

    added a README

commit 6e13d5a65e7bdc69c7584298691ba49edfc7a2c8
Author: l-isaro <l.isaro@alustudent.com>
:
```
6. **Dropping a Commit:**

   - We all make mistakes. Imagine needing to completely remove an unwanted commit from your history.

   - Create a new file named `unwanted.txt` add some changes and commit it with a message like "Unwanted commit".

   **Challenge:** Use `git rebase -i` to identify and remove the "Unwanted commit" commit, cleaning up your history. learn more about `dropping commits` [here](https://articles.assembla.com/en/articles/2941346-how-to-delete-commits-from-a-branch-in-git)
```
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git add unwanted.txt

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git commit -m "Unwanted commit"                     
[main 33c3513] Unwanted commit
 1 file changed, 0 insertions(+), 0 deletions(-)      
 create mode 100644 unwanted.txt

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase -i Head~3
Successfully rebased and updated refs/heads/main.     

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git log
commit e1de2554075b1ac298527fa23d2c343be7e0166a (HEAD 
-> main)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:33:06 2024 +0200

    Create third and fourth files

    Create Third File

    Create fourth file

commit 50fd728712c30d94cb7d27e072b1acf951db070a       
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:29:12 2024 +0200

    added a README

commit 6e13d5a65e7bdc69c7584298691ba49edfc7a2c8       
:
```

7. **Reordering Commits:**

   - Delve deeper into `git rebase -i`. Can you rearrange commits within your history using this command? learn more about `ordering commits` [here](https://www.youtube.com/watch?v=V9KpcGO7nLo)

```
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git log
commit e1de2554075b1ac298527fa23d2c343be7e0166a (HEAD 
-> main)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:33:06 2024 +0200
pick e1de255 Create third and fourth files

    Create third and fourth files

    Create Third File

    Create fourth file

commit 50fd728712c30d94cb7d27e072b1acf951db070a       
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:29:12 2024 +0200

    added a README

commit 6e13d5a65e7bdc69c7584298691ba49edfc7a2c8       

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git rebase -i Head~2
Successfully rebased and updated refs/heads/main.     

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git log
commit 264ea5b0c3d8300865262d08d33fbfe36d3c68eb (HEAD 
-> main)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:29:12 2024 +0200

    added a README

commit 749c78a6e6782e68e815ba4449bb4755dcb6539c       
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:33:06 2024 +0200

    Create third and fourth files

    Create Third File

    Create fourth file

commit 6e13d5a65e7bdc69c7584298691ba49edfc7a2c8       
:
```

8. **Cherry-Picking Commits:**

   - Create a branch, call it `ft/branch`, and add a new file named `test5.md` with some content. Commit these changes with a message like "Implemented test 5".
   - Imagine you only desire a specific commit from `ft/branch`. Research and use `git cherry-pick` to selectively bring that commit into your current branch which is `main`.

   learn more about `cherry-pick` [here](https://www.freecodecamp.org/news/git-cherry-pick-avoid-duplicate-commits/)

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/DocumSwitched to a new branch 'ft/branch'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/DocumSwitched to a new branch 'ft/branch'   

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Docum
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/branch)
$ touch test5.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/branch)
$ git add test5.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/branch)
$ git commit -m "Implemented test 5"
[ft/branch 4ed9be8] Implemented test 5
 1 file changed, 1 insertion(+)       
 create mode 100644 test5.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/branch)
$ git branch
* ft/branch
  main

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/branch)
$ git checkout main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)    
$ git log
commit 264ea5b0c3d8300865262d08d33fbfe36d3c68eb (HEAD -> main)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:29:12 2024 +0200

    added a README

commit 749c78a6e6782e68e815ba4449bb4755dcb6539c
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:33:06 2024 +0200

    Create third and fourth files

    Create Third File

    Create fourth file

commit 6e13d5a65e7bdc69c7584298691ba49edfc7a2c8
Author: l-isaro <l.isaro@alustudent.com>

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)    
$ git checkout ft/branch
Switched to branch 'ft/branch'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/branch)
$ git log
commit 4ed9be8484b8b4ef45d3588b33f09b15a7c2af86 (HEAD -> ft/branch)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Tue May 21 08:42:55 2024 +0200

    Implemented test 5

commit 264ea5b0c3d8300865262d08d33fbfe36d3c68eb (main)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:29:12 2024 +0200

    added a README

commit 749c78a6e6782e68e815ba4449bb4755dcb6539c
Author: l-isaro <l.isaro@alustudent.com>
Date:   Mon May 20 16:33:06 2024 +0200

    Create third and fourth files


ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/branch)
$ git checkout main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)    
$ git cherry-pick 4ed9be8484b8b4ef45d3588b33f09b15a7c2af86 
[main 1145b5a] Implemented test 5
 Date: Tue May 21 08:42:55 2024 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)    
$
```

9. **Visualizing Commit History (Bonus):**

   - Tools like `git log --graph` or a graphical Git client can help visualize your commit history. Explore these tools for a clearer understanding of your workflow.

```bash
git log --graph
*   commit 51ceaa42a48b59f2b5635b63e24b981a27834eff (HEAD -> main, origin/main, origin/HEAD)
|\  Merge: 1145b5a 2abf6fc
| | Author: l-isaro <l.isaro@alustudent.com>
| | Date:   Tue May 21 10:49:08 2024 +0200
| | 
| |     Merge branch 'main' of https://github.com/l-isaro/TheGymGitAdvanced
| | 
| * commit 2abf6fc437a90928bb272f3142e3cad7e993136b
| | Author: l-isaro <l.isaro@alustudent.com>       
| | Date:   Mon May 20 13:39:18 2024 +0200
| | 
| |     Created 4th file
| | 
| * commit dac17da95384b5610096e65ce44711874b4f3724
| | Author: l-isaro <l.isaro@alustudent.com>       
| | Date:   Mon May 20 13:38:31 2024 +0200
| | 
| |     chore: Create third and fourth files       
:
```

10. **Understanding Reflogs (Bonus):**

- Reflogs track Git operation history. Research about `git reflog` to learn how you can navigate back to previous states in your repository if needed.

**Part 2: Branching Basics (10 Challenges)**

1. **Feature Branch Creation:**

   - Imagine working on a new feature named `ft/new-feature`. Let's establish a dedicated branch for it.

   **Challenge:** Create a new branch named `ft/new-feature` and switch to that branch.
```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)   
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-feature)
$ 
```

2. **Working on the Feature Branch:**

   - Create a new file named `feature.txt` in this branch and add some content to it.
   - Commit these changes with a descriptive message like "Implemented core functionality for new feature".

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-feature)
$ touch feature.txt

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-feature)
$ git add feature.txt 

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-feature)
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature f35503c] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
```

3. **Switching Back and Making More Changes:**

   - It's common to switch between branches during development.

   **Challenge:** Switch back to the `main` branch (previously master) and create a new file named `readme.txt` with some introductory content. Commit these changes with a message like "Updated project readme".

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-feature)
$ git checkout main                           ymGitAdvanced (ft/new-f
Switched to branch 'main'
Your branch is up to date with 'origin/main'. 

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ touch readme.txt                            ymGitAdvanced (main)   

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)                          ymGitAdvanced (main)   
$ git add readme.txt

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git commit -m "Updated project readme"
[main a251949] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt
```

4. **Local vs. Remote Branches:**

   - So far, we've been working with local branches that exist on your machine. Research the concept of remote branches, which are copies of your local branches stored on a Git hosting platform like GitHub. [Learn](https://www.baeldung.com/ops/git-synchronize-local-remote-branches) how to push your local branches to remote repositories and pull changes from them to keep your local and remote repositories in sync.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads       
Compressing objects: 100% (2/2), done.        
Writing objects: 100% (3/3), 283 bytes | 141.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/l-isaro/TheGymGitAdvanced.git
   51ceaa4..a251949  main -> main
```

5. **Branch Deletion:**

   - After merging or completing work on a feature branch, it's good practice to remove it.

   **Challenge:** Delete the `ft/new-feature` branch once you're confident the changes are integrated into `main`.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git merge ft/new-feature
hint: Waiting for your editor to close the fil
Merge made by the 'ort' strategy.
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git branch -d ft/new-feature
Deleted branch ft/new-feature (was f35503c).

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$
```

6. **Creating a Branch from a Commit:**

   - You can also create a branch from a specific commit in your history.

   **Challenge:** Use `git checkout -b ft/new-branch-from-commit commit-hash` (adjust the commit hash as needed) to create a new branch named `ft/new-branch-from-commit` starting from the commit two positions back in your history. learn more [here](https://www.novicedev.com/blog/create-git-branch-commit)

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git log
commit cb10abc52af6d773eacd8ad43e900e7b617c0f76 (HEAD -> main)
Merge: a251949 f35503c
Author: l-isaro <l.isaro@alustudent.com>
Date:   Tue May 21 12:10:21 2024 +0200

    Merge branch 'ft/new-feature'

commit a2519499c58400f8cf076a1bb6e2a17658572fcd (origin/main, origin/HEAD)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Tue May 21 11:57:18 2024 +0200

    Updated project readme

commit f35503c1b51e2a4bacd04d4a4c57e4ba0da2d937
Author: l-isaro <l.isaro@alustudent.com>
Date:   Tue May 21 11:49:27 2024 +0200
cb10abc (HEAD -> main) Merge branch 'ft/new-feature'                                        ture
a251949 (origin/main, origin/HEAD) Updated project readme                                   ymGitAdvanced (main)
f35503c Implemented core functionality for new feature                                      ature'
51ceaa4 Merge branch 'main' of https://github.ject readmecom/l-isaro/TheGymGitAdvanced                  feature
1145b5a Implemented test 5                    com/l-isaro/TheGymGitAdvanced
264ea5b added a README
749c78a Create third and fourth files
2abf6fc Created 4th file
dac17da chore: Create third and fourth files  
6e13d5a chore: create initial file
762e148 Initial commit

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)                          ymGitAdvanced (main)
$ git checkout -b ft/new-branch-from-commit a2519499c58400f8cf076a1bb6e2a17658572fcd        
Switched to a new branch 'ft/new-branch-from-commit'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-branch-from-commit)     
$
```

7. **Branch Merging:**

   - Now that you've completed work on your feature branch, it's time to integrate it into `main`.

   **Challenge:** Merge the `ft/new-branch-from-commit` branch into the `main` branch. Address any merge conflicts that might arise.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-branch-from-commit)     
$ git merge ft/new-branch-from-commit
Already up to date.
```

8. **Branch Rebasing:**

   - Rebasing is another method to integrate changes from a feature branch. It rewrites your branch history by incorporating its commits on top of the latest commit in the target branch (`main` in our case).

   **Challenge:** Try rebasing the `ft/new-branch-from-commit` branch onto the `main` branch. Remember, rebasing rewrites history, so use it with caution, especially in shared repositories. learn more about rebasing [here](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase#:~:text=From%20a%20content%20perspective%2C%20rebasing,them%20to%20the%20specified%20base.)

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)   
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-branch-from-commit)ranch-from-commit)
$ git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
```

9. **Renaming Branches:**

   - Branch names can sometimes evolve. Let's rename `ft/new-branch-from-commit` to a more descriptive name.

   **Challenge:** Use `git branch -m ft/new-branch-from-commit ft/improved-branch-name` to rename your branch.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/new-branch-from-commit)
$ git branch -m ft/new-branch-from-commit ft/improved-branch-name

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$
```

10. **Checking Out Detached HEAD:**

- In specific situations, you might need to detach HEAD from your current branch. Research `git checkout <commit-hash>` (replace with the desired commit hash) to understand this concept.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git checkout a2519499c58400f8cf076a1bb6e2a17658572fcd
Note: switching to 'a2519499c58400f8cf076a1bb6e2a17658572fcd'.

You are in 'detached HEAD' state. You can look around, make experimental 
changes and commit them, and you can discard any commits you make in thisstate without impacting any branches by switching back to a branch.      

If you want to create a new branch to retain commits you create, you may 
do so (now or later) by using -c with the switch command. Example:       

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at a251949 Updated project readme

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced ((a251949...))
$ git switch -
Previous HEAD position was a251949 Updated project readme
Switched to branch 'ft/improved-branch-name'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$
```

**Part 3: Advanced Workflows (10+ Challenges)**

1. **Stashing Changes:**

   - Imagine you're working on some changes in the `main` branch but need to attend to something urgent. You don't want to lose your uncommitted work.

   **Challenge:** Stash your current changes in the `main` branch using `git stash`.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git status
On branch ft/improved-branch-name
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)  
        modified:   test1.md

no changes added to commit (use "git add" and/or "git commit -a")        

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git stash
Saved working directory and index state WIP on ft/improved-branch-name: cb10abc Merge branch 'ft/new-feature'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git status
On branch ft/improved-branch-name
nothing to commit, working tree clean
```

2. **Retrieving Stashed Changes:**

   - Later, when you're ready to resume working on those stashed changes, you can retrieve them.

   **Challenge:** Apply the most recent stash back onto the `main` branch using `git stash pop`.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git stash pop
On branch ft/improved-branch-name
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)  
        modified:   test1.md

no changes added to commit (use "git add" and/or "git commit -a")        
Dropped refs/stash@{0} (ff64a085dfd6e193311aa1c7bdde25a030991f04)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
```

3. **Branch Merging Conflicts (Continued):**

   - Merge conflicts can arise when the same lines of code are modified in both branches being merged.

   **Challenge:** Simulate a merge conflict scenario (you can create conflicting changes in a file on both `main` and a new feature branch). Then, try merging again and resolve the conflicts manually using your text editor.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git checkout ft/new-feature
error: pathspec 'ft/new-feature' did not match any file(s) known to git

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git branch
  ft/branch
* ft/improved-branch-name
  main

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git checkout ft/improved-branch-name
M       test1.md
Already on 'ft/improved-branch-name'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git checkout main
M       test1.md
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test1.md

no changes added to commit (use "git add" and/or "git commit -a")

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git merge ft/improved-branch-name
Already up to date.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git add test1.md 

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git commit -m "added text to the text1 file"
[main 435acaa] added text to the text1 file
 1 file changed, 1 insertion(+)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git checkout ft/improved-branch-name
Switched to branch 'ft/improved-branch-name'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git status
On branch ft/improved-branch-name
nothing to commit, working tree clean

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git status
On branch ft/improved-branch-name
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   test1.md

no changes added to commit (use "git add" and/or "git commit -a")

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git add test1.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git commit -m "added content to the text1 file"
[ft/improved-branch-name 7c99324] added content to the text1 file
 1 file changed, 1 insertion(+)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git merge ft/improved-branch-name
Auto-merging test1.md
CONFLICT (content): Merge conflict in test1.md
Automatic merge failed; fix conflicts and then commit the result.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main|MERGING)
$ git staus
git: 'staus' is not a git command. See 'git --help'.

The most similar command is
        status

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 5 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git log
commit 04614c488f05f619409eebab9814fa4f85922417 (HEAD -> main)
Merge: 435acaa 7c99324
Author: l-isaro <l.isaro@alustudent.com>
Date:   Tue May 21 17:01:09 2024 +0200

    Merge branch 'ft/improved-branch-name'

commit 7c99324f4596b113e941872146c08cbc4f572881 (ft/improved-branch-name)
Author: l-isaro <l.isaro@alustudent.com>
Date:   Tue May 21 17:00:14 2024 +0200

    added content to the text1 file

commit 435acaa969f83abbe33bdd184c682132dd09f88c
Author: l-isaro <l.isaro@alustudent.com>
Date:   Tue May 21 16:56:12 2024 +0200

    added text to the text1 file
:
```

4. **Resolving Merge Conflicts with a Merge Tool:**

   - Explore using a merge tool like `git mergetool` to help you visualize and resolve merge conflicts more efficiently.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
opendiff kdiff3 tkdiff xxdiff meld tortoisemerge gvimdiff diffuse diffmerge ecmerge p4merge araxis bc codecompare smerge emerge vimdiff nvimdiff
No files need merging

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git merge ft/improved-branch-name
Already up to date.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git checkout ft/improved-branch-name 
Switched to branch 'ft/improved-branch-name'

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ ls
feature.txt  README.md  readme.txt  test1.md  test2.md  test3.md  test4.md  test5.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git add test1.md

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git commit -m "added more content to the first "
[ft/improved-branch-name d0a9eaf] added more content to the first
 1 file changed, 1 insertion(+), 1 deletion(-)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 6 commits.
  (use "git push" to publish your local commits)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git merge ft/improved-branch-name
Auto-merging test1.md
CONFLICT (content): Merge conflict in test1.md
Automatic merge failed; fix conflicts and then commit the result.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main|MERGING)
$ git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
opendiff kdiff3 tkdiff xxdiff meld tortoisemerge gvimdiff diffuse diffmerge ecmerge p4merge araxis bc codecompare smerge emerge vimdiff nvimdiff
Merging:
test1.md

Normal merge conflict for 'test1.md':
  {local}: modified file
  {remote}: modified file
Hit return to start merge resolution tool (vimdiff):
4 files to edit

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main|MERGING)
$ git merge ft/improved-branch-name
fatal: You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you merge.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main|MERGING)
$ git commit -m "merging"
[main 2115a07] merging

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git merge ft/improved-branch-name
Already up to date.

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$
```

5. **Understanding Detached HEAD State:**

   - Detached HEAD refers to a state where your working directory is not associated with any specific branch. Research the implications and how to recover from this state using commands like `git checkout <branch-name>`.

6. **Ignoring Files/Directories:**

   - You might have files or directories you don't want to track in Git. Create a `.gitignore` file to specify these exclusions.

   **Challenge:** Add a pattern like `/tmp` to your `.gitignore` file to exclude all temporary files and directories from version control. more about `ignoring files` [here](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files)

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ touch .gitignore

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git add .gitignore 

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git commit -m "added a gitignore file"
[ft/improved-branch-name 06c09cf] added a gitignore file
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$
```

7. **Working with Tags:**

   - Tags act like bookmarks in your Git history. Create a tag to mark a specific point in your development.

   **Challenge:** Use `git tag v1.0` to create a tag named `v1.0` on the current commit in your `main` branch. [git tags](https://www.javatpoint.com/git-tags)

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git chekout main
Merge branch 'ft/improved-branch-name'
git: 'chekout' is not a git command. See 'git --help'.

The most similar command is
        checkout

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (ft/improved-branch-name)
$ git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 9 commits.
  (use "git push" to publish your local commits)  

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git merge ft/improved-branch-name
hint: Waiting for your editor to close the file...
Merge made by the 'ort' strategy.
 .gitignore | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git tag v1.0

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$
```

8. **Listing and Deleting Tags:**

   **Challenge:** Use `git tag` to list all existing tags. Then, use `git tag -d <tag-name>` to delete a specific tag (replace `<tag-name>` with the actual tag you want to remove).

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)       
$ git tag
v1.0

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)
$ git tag -d v1.0
Deleted tag 'v1.0' (was 91f2a57)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)       
$
```

9. **Pushing Local Work to Remote Repositories:**

   - Once you're happy with your local changes and branches, it's time to share them with others.

   **Challenge:** Assuming you've set up a remote repository on a Git hosting platform (like GitHub), push the changes with the actual branch you want to push to push your local branch to the remote repository.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)       
$ git push origin main
Enumerating objects: 32, done.
Counting objects: 100% (31/31), done.
Delta compression using up to 4 threads
Compressing objects: 100% (22/22), done.
Writing objects: 100% (28/28), 2.39 KiB | 84.00 KiB/s, done.
Total 28 (delta 12), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (12/12), completed with 1 local object.   
To https://github.com/l-isaro/TheGymGitAdvanced.git
   a251949..91f2a57  main -> main

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)       
$
```

10. **Pulling Changes from Remote Repositories:**

- Collaboration often involves pulling changes from the remote repository made by others.

**Challenge:** Navigate to Github and make some changes inside your `README` file that you created on your `main` branch and in your local environment use `git pull origin <branch-name>` (replace `<branch-name>` with the actual branch you want to pull) to fetch changes from the remote repository's `main` branch and merge them into your local `main` branch. Address any merge conflicts that might arise.

```bash
ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)       
$ git pull origin main
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 941 bytes | 52.00 KiB/s, done.
From https://github.com/l-isaro/TheGymGitAdvanced
 * branch            main       -> FETCH_HEAD
   91f2a57..b3fb35a  main       -> origin/main
Updating 91f2a57..b3fb35a
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)

ISARO@DESKTOP-JAF8I5H MINGW64 ~/Documents/TheGymGitAdvanced (main)       
$
```
