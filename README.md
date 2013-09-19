git-edit-wrapper
================

A simple bash script that wraps around your editor of choice to automate git commits after an edit

This should work with any command line editor (uemacs, em, vi, emacs, joe, etc) and does the following..

If precommit is set to 1 and there is a git repo or autogit=1, we check in existing files into the git
repo before we start editing so we have immediate change history.

Then using git if possible or falling back on md5sum the script checks to see if the file has changed at
all, we then look to see if there is an available git repo to check the file into.  If not and autogit is
set to 1, we create a git repo.  We then do git add and prmopt the user for a commit message.

Configuration..

editor=/path/to/your/favorite/editor
pager=/path/to/your/favorite/pager

restorecon=/path/to/restorecon (if using selinux)
getenforce/path/to/getenforce (if using selinux)

autogit=1 (If you want it to automatically create a repo if one does not yet exist)

precommit=1 (If you want it to commit the original file before editing if a repo exists or can be created (autogit=1)

autogit and precommit are independent options, however precommit cannot check in a file before editing if autogit
is not set to 1 and there isn't an existing repo.

Hope it's useful to someone!

History..

I've used microEmacs since the AmigaDOS days, which was called the "Advanced Editor".  When I moved to
Linux in the late 90's I quickly found microEmacs 3.12 which operated exactly the same way it did in
AmigaDOS.  Newer versions changed some of the key sequences around so I've used the same binary for
years now.  Problem?  Clobbers symlinks..  Clobbers selinux..  So I wrote a wrapper to work around
these issues.

Recently I decided that even though I still don't really understand git well enough (see my screwy
commit log for fine examples of that) I decided that even though I have a snapshot of my hard drive
four times a day I still could use more granularity and history when I'm editing things, particularly
config files, scripts, code...  But then I realized I'd never do it consistently enough unless I
was forced to, so I added git logic to my wrapper script.

I've since cleaned it up a little, made it a little less "uemacs-centric" (even though the original
name remains; 'me') and added some configurability for if using SELinux, to automatically create a
git repo, etc.
