.. _10_cfg_mgt:

Configuration Management History & Basics
=========================================


DevOps workflow in an agency environment
----------------------------------------

Greg Lund-Chaix

.. image:: ../_static/squishy.png

Director of Technology

http://squishymedia.com


Tools @ Squishy
---------------

* GitLab & GitLab CI - http://gitlab.com
* Puppet - http://puppetlabs.com
* Vagrant - http://vagrantup.com

Workflow @ Squishy
------------------

Repository layout:

.. rst-class:: codeblock-sm

::

  [repo root]
  ├── .git
  ├── bin
  │   └── deploy.sh
  ├── core
  │   └── drupal-7.x
  ├── data
  ├── docs
  ├── htdocs -> core/drupal-7.x
  ├── private
  ├── README.md
  ├── tests
  │   ├── app
  │   └── e2e
  ├── vagrant
  │   ├── manifests
  │   └── modules
  └── Vagrantfile

Workflow @ Squishy
------------------

* Clone & create new branch
* Develop & test locally using Vagrant (if needed)
* Push to GitLab & create merge (pull) request to master

  - CI runs all tests in the tests directory on every push

* Code review by another team member, approve merge/pull request
* Push to master with all tests passsing triggers a deploy to staging via bin/deploy.sh
* Deployment to production is currently manual

What works?  What doesn't?
--------------------------

* Puppet & Vagrant
* Code review
* CI & Drupal
