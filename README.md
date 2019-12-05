# How to add new version of civicrm to repository

* \# copy to text editor, set VERSION variable, copy commands to terminal & Engage!
* VERSION='5.19.4'
* git checkout master
* git checkout -b civicrm-$VERSION.vanilla
* git clean -f -d
* wget https://download.civicrm.org/civicrm-$VERSION-drupal.tar.gz
* tar -xvzf civicrm-$VERSION-drupal.tar.gz
* rm civicrm-$VERSION-drupal.tar.gz
* cd civicrm/ && mv * ../ && cd .. && rm civicrm/ -R
* git add *
* git commit -m "CiviCRM $VERSION Vanilla"
* git push -u origin civicrm-$VERSION.vanilla
* git checkout -b civicrm-$VERSION.patched
* git push -u origin civicrm-$VERSION.patched
* \# add patches, look at below...

# How to add patches to new clean patched branch

There're several possibilities how to add our custom patches.

* git checkout civicrm-PREVIOUS-VERSION.patched
* git fetch, git pull
* open list of commits of current patched branch
    * `git log --reverse` on separate console window
        * `git log --reverse | grep "^commit " | sed 's/commit /git cherry-pick /' # apply from 3rd line to bottom commit by commit`
* git checkout civicrm-VERSION.patched
* apply patches starting from the oldest to the newest
    * check if patch is already merged into core (official issues)
    * git cherry-pick HASH-COMMIT
    * `git cherry-pick --continue` after fixing known conflicts
    * `git cherry-pick --abort` in case of conflict (patch could be already merged in VERSION)
    * `git reset` in case of commit already patched in core
* git push

# How to create new patch

Example for editing Mailing.php class

* git checkout civicrm-4.7.20.vanilla
* git checkout -b patch.crm-19236
* vi CRM/Mailing/BAO/Mailing.php
* git commit -a -m "(patch.crm-19236) URL with unicode signs breaks down trackable urls"
* git push origin patch.crm-19236
* git log -1    // in order to display commit hash
* git checkout civicrm-4.7.20.patched
* git fetch
* git status
* git pull origin civicrm-4.7.20.patched // only when needed
* git cherry-pick df56948ac66bffa540854de4c2148d64da7f155d   // commit hash
* git push origin civicrm-4.7.20.patched

## Branch template for patch

* `core-99999` for reported issues
* `patch.WORDS-SEPARATED-BY-DASHES` for our patches
