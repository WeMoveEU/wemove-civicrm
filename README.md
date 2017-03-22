![](i/logo_lg.png) Welcome to CiviCRM
=====================================

About
-----

CiviCRM is a constituent relationship management system designed to
meet the needs of advocacy, non-profit and non-governmental groups.
It is an open source project, licensed under GNU AGPL 3, and
coordinated by CiviCRM LLC. The project website is https://civicrm.org/

CiviCRM is released as a module that runs within the Drupal, Joomla,
and WordPress content management systems.


Installation
------------

The download URLs and installation instructions are available on our website:
https://civicrm.org/download

Detailed installation instructions are [on the wiki](https://wiki.civicrm.org/confluence/display/CRMDOC/Installation+and+Upgrades).


Documentation
-------------

Documentation can be found at https://civicrm.org/documentation


Support
-------

Answers for users, administrators & integrators:
http://civicrm.stackexchange.com

Paid support available from
https://civicrm.org/providers


Development and Bugs
--------------------

Developers are highly encouraged to join [chat.civicrm.org](https://chat.civicrm.org) and post
questions and ideas in the [Developer Discussion room](https://chat.civicrm.org/civicrm/channels/dev).

Installing the latest developmental code requires some [special steps](http://wiki.civicrm.org/confluence/display/CRMDOC/Contributing+to+CiviCRM+using+GitHub). 

Report all issues to CiviCRM via GitLab:
https://lab.civicrm.org


Fix after upgrade to 4.7.17
---------------------------

cd /var/www/drupal/sites/default/files
sudo mkdir civicrm && cd civicrm && sudo mkdir persist && cd persist
sudo ln -s /var/www/drupal/sites/wemove/files/civicrm/persist/crm-ckeditor-default.js crm-ckeditor-default.js
