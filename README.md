# How to add new version of civicrm to repository

* git checkout master
* git checkout -b civicrm-VERSION.vanilla
* wget VERSION
    * wget https://download.civicrm.org/civicrm-4.7.17-drupal.tar.gz
* unzip
    * tar -xvzf civicrm-4.7.17-drupal.tar.gz
* git add *
* git commit -m "CiviCRM VERSION Vanilla"
* git push origin civicrm-VERSION.vanilla
* git checkout -b civicrm-VERSION.patched
* git push origin civicrm-VERSION.patched


# How to create new patch

Example for editing Mailing.php class

* git checkout civicrm-4.6.23.vanilla
* git checkout -b patch-crm-19236
* vi CRM/Mailing/BAO/Mailing.php
* git commit -a -m "(patch-crm-19236) URL with unicode signs breaks down trackable urls"
* git push origin patch-crm-19236
* git log -1    // in order to display commit hash
* git checkout civicrm-4.6.23.patched
* git cherry-pick df56948ac66bffa540854de4c2148d64da7f155d   // commit hash
* git push origin civicrm-4.6.23.patched

