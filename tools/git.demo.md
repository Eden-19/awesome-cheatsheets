# Demo sync fork

## Cloniamo i repository
┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx]
└─$ git clone https://github.com/xxxP3g4s0xxx/awesome-cheatsheets.git
Cloning into 'awesome-cheatsheets'...
remote: Enumerating objects: 2445, done.
remote: Counting objects: 100% (25/25), done.
remote: Compressing objects: 100% (23/23), done.
remote: Total 2445 (delta 7), reused 14 (delta 2), pack-reused 2420
Receiving objects: 100% (2445/2445), 7.69 MiB | 3.96 MiB/s, done.
Resolving deltas: 100% (1423/1423), done.

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx]
└─$ cd awesome-cheatsheets

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git remote set-url origin git@github.com:xxxP3g4s0xxx/awesome-cheatsheets.git

## Aggiungiamo un repository remoto
┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git remote add upstream git@github.com:xxxDevNullxxx/awesome-cheatsheets.git

Please make sure you have the correct access rights
and the repository exists.

## Reuperiamo i metadati
┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git fetch upstream
From github.com:xxxDevNullxxx/awesome-cheatsheets
 * [new branch]      master     -> upstream/master

## Aggiungiamo un file in locale
┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ vi tools/git.demo.md

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git log --remotes
commit 715ab0b140870868713f10f3f7c7bb2cd5e55787 (HEAD -> master, upstream/master, origin/master, origin/HEAD)

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ vi tools/git.demo.md

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        tools/git.demo.md

nothing added to commit but untracked files present (use "git add" to track)

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git add .

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git commit -m "Aggiunto git.demo.md"
[master 3d4044f] Aggiunto git.demo.md
 1 file changed, 26 insertions(+)
 create mode 100644 tools/git.demo.md

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git log
commit 3d4044fd2e939ee1e8d71bb1ffae8d345c3f65e7 (HEAD -> master)
Author: Oscar Ibattici <oibattici@sidesoft.it>
Date:   Wed Sep 27 16:37:54 2023 +0200

    Aggiunto git.demo.md

commit 715ab0b140870868713f10f3f7c7bb2cd5e55787 (upstream/master, origin/master, origin/HEAD)
Author: UT0SIDV <UT0SIV@GROUP.CREDEM.NET>
Date:   Wed Sep 27 13:39:34 2023 +0200

    Added syncing-a-fork example



## Nel repository di up stream effettuiamo una modifica

## Procediamo con il sync

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git fetch upstream
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 2), reused 3 (delta 2), pack-reused 0
Unpacking objects: 100% (3/3), 303 bytes | 101.00 KiB/s, done.
From github.com:xxxDevNullxxx/awesome-cheatsheets
   715ab0b..8d87988  master     -> upstream/master

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git log --remotes
commit 8d879881ee8e64e142f7d3f59f5594a28547bff6 (upstream/master)
Author: DevNull <devnull.127.0.0.1@gmail.com>
Date:   Wed Sep 27 16:45:09 2023 +0200

    Commit post fork

commit 715ab0b140870868713f10f3f7c7bb2cd5e55787 (origin/master, origin/HEAD)
Author: UT0SIDV <UT0SIV@GROUP.CREDEM.NET>
Date:   Wed Sep 27 13:39:34 2023 +0200

    Added syncing-a-fork example

## Eseguiamo il merge
┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git merge upstream/master --autostash
Created autostash: 88cc5c8
Merge made by the 'ort' strategy.
 README.md | 1 +
 1 file changed, 1 insertion(+)
Applied autostash.

┌──(oscar㉿NB-OSCAR)-[~/xxxP3g4s0xxx/awesome-cheatsheets]
└─$ git status
On branch master
Your branch is ahead of 'origin/master' by 3 commits.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   tools/git.demo.md

no changes added to commit (use "git add" and/or "git commit -a")
