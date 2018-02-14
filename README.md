# How to add new version of civicrm to repository

* git checkout master
* git checkout -b civicrm-VERSION.vanilla
* git clean -f -d
* wget VERSION
    * wget https://download.civicrm.org/civicrm-4.7.20-drupal.tar.gz
* unzip
    * tar -xvzf civicrm-4.7.20-drupal.tar.gz
* copy files from unzipped subdirectory
    * rm civicrm-4.7.20-drupal.tar.gz
    * cd civicrm/ && mv * ../ && cd .. && rm civicrm/ -R
* git add *
* git commit -m "CiviCRM VERSION Vanilla"
* git push origin civicrm-VERSION.vanilla
* git checkout -b civicrm-VERSION.patched
* git push -u origin civicrm-VERSION.patched

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

* `crm-99999` for reported issues
* `patch.WORDS-SEPARATED-BY-DASHES` for our patches

# How to add patches to new clean patched branch

There're several possibilities how to add our custom patches.

* git checkout civicrm-PREVIOUS-VERSION.patched
* git fetch, git pull
* open list of commits of current patched branch
    * `git log` on separate console window
    * copy the list to text editor, will be a checklist what you have to check
    * apply patches starting from the oldest to the newest
* git checkout civicrm-VERSION.patched
* git cherry-pick HASH-COMMIT  // choose hash from list of commits from current branch
    * `git cherry-pick --continue` after fixing known conflicts
    * `git cherry-pick --abort` in case of conflict (patch could be already merged in VERSION)
    * `git reset` in case of commit already patched in core

