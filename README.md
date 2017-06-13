# How to add new version of civicrm to repository

* git checkout master
* git checkout -b civicrm-VERSION.vanilla
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
* git push origin civicrm-VERSION.patched


# How to create new patch

Example for editing Mailing.php class

* git checkout civicrm-4.7.20.vanilla
* git checkout -b patch.crm-19236
* vi CRM/Mailing/BAO/Mailing.php
* git commit -a -m "(patch.crm-19236) URL with unicode signs breaks down trackable urls"
* git push origin patch.crm-19236
* git log -1    // in order to display commit hash
* git checkout civicrm-4.7.20.patched
* git cherry-pick df56948ac66bffa540854de4c2148d64da7f155d   // commit hash
* git push origin civicrm-4.7.20.patched

## Branch template for patch

* `crm-99999` for reported issues
* `patch.WORDS-SEPARATED-BY-DASHES` for our patches

# How to add patches to new clean patched branch

There're several possibilities how to add our custom patches.

* open list of commits of current patched branch. This will be a checklist what you have to check.
    * `git log` on separate console window
* git checkout civicrm-VERSION.patched
* git cherry-pick HASH-COMMIT  // choose hash from list of commits from current branch
    * `git cherry-pick --abort` in case of conflict (patch could be already merged in VERSION)

