## Getting Git

### Windows

![](Git-clone-gui.png "Git-clone-gui.png")
![](Git-clone-gui-step2.png "Git-clone-gui-step2.png")

Install and or install the official Git (see the msysGit link) and use
the official Git GUI.

Use the msys batch file in the msysGit directory to get the mingw shell
and execute all the commands below (if you are not using TortoiseGit and
would like to deal with Git on the commandline)

### Mac OS X

Get git-core through

### Linux

If you are under [Linux](Linux "wikilink") git should be installable via
your package manager.

## Write support

To get the repository with write support, type:

`git remote set-url --push origin `[`ssh://`](ssh://)<SF-username>`@git.code.sf.net/p/ufoai/code`

#### Git Bundle

Our repo is very large. If you're having trouble cloning it all in one
go, you can download a git bundle via torrent
![<File:UFO-Alien-Invasion-master-01d1bbf-2013-06-17.bundle.torrent>](UFO-Alien-Invasion-master-01d1bbf-2013-06-17.bundle.torrent "File:UFO-Alien-Invasion-master-01d1bbf-2013-06-17.bundle.torrent")

Then run these commands to clone from the bundle:

`git init ufoai`
`cd ufoai`
`git pull ../ufoai-master-01d1bbf-2013-06-17.bundle master`
`git remote add origin `[`git://git.code.sf.net/p/ufoai/code`](git://git.code.sf.net/p/ufoai/code)` --track master`
`git pull`

More detailed instructions were posted in [our
forums](http://ufoai.org/forum/index.php/topic,7797.0.html).

#### Config

For non-global options you have to into your git checkout directory
first.

`git config --global user.name "Your Name"`
`git config --global user.email mail@example.com`
`git config --global alias.upbase "rebase '@{u}'"`
`git config --global alias.wu "log --stat origin..@{0}"`
`git config --global push.default tracking`
`git config --global core.excludesfile '~/.gitignore'`
`echo "*~" >> ~/.gitignore`
`git config --global color.branch auto`
`git config --global color.diff auto`
`git config --global color.interactive auto`
`git config --global color.status auto`

To always rebase on a pull do this:

`git config branch.master.rebase true`

#### Creating a patch

If you commited them already and would like to create a patch from the
latest revision:

`git format-patch HEAD~`

If you would like to make patches for your last three revisions:

`git format-patch HEAD~3`

#### Applying patches

`git am patch.diff`

Note that it will create a commit, or even sets of commits from that
patch. On the other hand, git will create the ORIG_HEAD label that will
allow you to remove those commits in case you don't want them.

#### Removing patches

If you did not commit anything after applying the patch:

`git reset --hard ORIG_HEAD`

(note that reset --hard will kill your uncommitted work!!)

#### Stash local changes

If you have uncommited modification that you would like to keep, you can
stash them, do whatever you need a clean working copy for and pop the
changes back into your working copy when you are done.

`git stash save`

Do you changes here...

`git stash pop`

#### Show local commits

Shows local commits that are not yet part of the tracking branch:

`git cherry -v`

#### Creating a branch

Create a branch that tracks the current active branch. If you are e.g.
in master, your new created branch will track master.

`git branch -t BRANCHNAME`

Publish this branch

`git push origin master:BRANCHNAME`

#### Subsequent uses of the command

`git fetch`

will update your copy of the source and

`git upbase`

will merge your changes in. If there are conflicts you have to resolve
them and call

`git add FILE`

to mark the file as resolved. After that the rebase must be continued
with:

`git rebase --continue`

to push the local changes from the fix branch to the remote master
branch:

`git push origin fix:master`

`git log`

in the same directory presents you a log of recent changes.

`git commit`

commit changes to your local git repository

`git push`

pushes your commits to the global git repository.

`git checkout .`

reverts your local/uncommited changes.

`git reset --hard HEAD~`

completely reverts the last commit in your local repository to the
predecessor of HEAD (branch, index and working copy)

`git reset --soft HEAD~`

reverts the last commit in your local repository without reverting the
changed files to the predecessor of HEAD (branch, index and working
copy) - use that command to prevent losing changes made to files in the
commit you revert

`git init buildbot`
`cd buildbot`
`git fetch `[`git://git.code.sf.net/p/ufoai/code`](git://git.code.sf.net/p/ufoai/code)` buildbot:buildbot`
`git checkout buildbot`

Only fetches the buildbot branch.

`git rebase --whitespace=fix origin/master`

Fixes whitespaces in all of your local commits.

`git init buildbot; cd !$; git remote add -t buildbot origin `[`git://git.code.sf.net/p/ufoai/code`](git://git.code.sf.net/p/ufoai/code)`; git fetch; git co buildbot`

Fetches only the buildbot branch and tracks the remote buildbot branch.

#### Getting help

Shows all available git commands:

`git help --all`

### Next steps

- [Compiling the source](Coding#Compiling_the_source "wikilink")
- [Compiling the maps](Mapping/Compile "wikilink")
- [Compiling the language
  files](Translating#Compile_the_language_files "wikilink")

## github

There is a [github](https://github.com/ufoai) mirror which you can use
for cloning, too. Using this mirror could be a preferred option if you
have slow internet connection, because github allows longer download
times than SourceForge. To clone repository from github mirror, use this
command:

`git clone --progress `[`git://github.com/ufoai/ufoai.git`](git://github.com/ufoai/ufoai.git)

If you want this clone to track SourceForge repository, enter following
commands after cloning completes:

`cd ufoai`
`git config remote.origin.url `[`git://git.code.sf.net/p/ufoai/code`](git://git.code.sf.net/p/ufoai/code)

Please also note that github mirror tracks only the master branch. You
will have to use SourceForge to fetch any other branches.

## rsync way

Also it is possible to get repo via the \[ rsync\] utility. Use it if
your network doesn\`t allow to load whole repo via git.

`rsync -av git.code.sf.net::p/ufoai/* $PATH_TO_RSYNC_TARGET_DIR `

After the fetching you need to do some more things:
1. rename code.git to .git
2. edit .git/config and set bare to false
3. go into ufoai and checkout your working copy
git remote set-url --push origin
<ssh://><SF-username>@git.code.sf.net/p/ufoai/code

`git remote set-url origin `[`git://git.code.sf.net/p/ufoai/code`](git://git.code.sf.net/p/ufoai/code)

## Webclient

There is also a [GIT Webclient](http://ufoai.git.sourceforge.net/) to
browse the repository with your webbrowser.

## External Links

- [ciabot](http://cia.vc/stats/project/ufoai)

## Git config

`[alias]`
`abort = rebase --abort`
`amend = commit --amend`
`ann = annotate`
`ada = add -A`
`adu = add -u`
`bvv = branch -vv`
`cat = cat-file -p`
`ci = commit -a`
`co = checkout`
`conflict = !$EDITOR -c '/^[<=|>]\\{7\\}\`$\\|$\$`` ' `git ls-files --unmerged | cut -c 51- | uniq` ``
`contains = branch -a --contains`
`continue = !git adu && git rebase --continue`
`cox = checkout-index`
`cx = commit`
`da = diff HEAD`
`dci = svn dcommit`
`di = diff`
`dx = diff --cached`
`drop = stash drop`
`gn = grep -In`
`graph = log --decorate --graph`
`gw = grep -Inw`
`less = -p cat-file -p`
`lg = log --decorate --graph --name-status`
`lg1 = log --decorate --graph --oneline`
`list = stash list`
`pop = stash pop`
`save = stash save`
`sf = svn fetch -q`
`skip = rebase --skip`
`st = status -s`
`tar = archive --format=tar`
`upbase = rebase '@{u}'`
`updiff = log -p --reverse @{u}..`
`upstream = branch --set-upstream`
`[core]`
`excludesfile = ~/.gitignore`
`pager = less -x 2 -R`
`[diff]`
`renames = copies`
`[gc]`
`#auto = 0`
`[merge]`
`conflictstyle=diff3`
`[push]`
`default=tracking`
`[user]`
`email = YOUR_MAIL`
`name = YOUR_NAME`

## Links

- [For SVN users](http://git.or.cz/course/svn.html)
- [Git Book](http://progit.org/book/)
- [Git Guide](http://wiki.sourcemage.org/Git_Guide)

[Category:Contribute](Category:Contribute "wikilink")
[Category:Coding](Category:Coding "wikilink")
[Category:Development](Category:Development "wikilink")