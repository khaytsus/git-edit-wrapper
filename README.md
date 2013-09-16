git-edit-wrapper
================

A simple bash script that wraps around your editor of choice to automate git commits after an edit

This should work with any command line editor (uemacs, em, vi, emacs, joe, etc) and does the following..

Using md5sum to see if the file has changed at all, we then look to see if there is an available git
repo to check the file into.  If not and autogit is set to 1, we create a git repo.  We then do git add
and prmopt the user for a commit message.
