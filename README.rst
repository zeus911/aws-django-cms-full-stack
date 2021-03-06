A full django stack with django cms

* elastic beanstalk using instanceprofile for credential rotation
* almost fits into free tier with single instance (redis is one cache node too many)
* aws managed elasticsearch for haystack
* aws managed redis for celery
* aws managed memcache
* aws managed postgres db

WIP: Making a HA setup in cloudformation/vpc-nat-ha, using aws managed nat (vpc complete now).

To deploy existing app in django/
=================================

Install `nodejs`_ or `io.js`_ and `Python`_.

::

  pip install awscli
  npm install
  aws configure
  gulp configure
  gulp deploy_lambda_resources
  gulp deploy_full_stack

Full deploy takes about 30 min, lambda resource for elasticsearch is slow.

Go to beanstalk console and visit the url /admin/ to add the first page.

Add another page with the search apphook, publish it and restart the app servers in the beanstalk console.

To build css/javascript
=======================

Install `nodejs`_ or `io.js`_.

Install node modules: ::

  npm install
  npm install -g bower

Install bower assets: ::

  bower install

Pasteable commands: ::

  npm install
  npm install -g bower
  bower install
  gulp build 
  
To run project locally
======================

Install `nodejs`_ or `io.js`_ and `Python`_.

Install node modules needed: ::

  npm install

Install virtualenv: ::
  
  pip install virtualenv

Create virtualenv: ::

  virtualenv env

Install python modules: ::

  env/bin/pip install -r requirements-dev.txt

Sync django database: ::

  env/bin/python django/manage.py syncdb

Pasteable commands (linux): ::

  pip install virtualenv

  virtualenv env
  env/bin/pip install -r requirements-dev.txt
  env/bin/python django/manage.py syncdb
  gulp serve

Pasteable commands (win): ::
  
  pip install virtualenv

  virtualenv env
  env\Scripts\pip.exe install -r requirements-dev.txt
  env\Scripts\python.exe django\manage.py syncdb
  gulp serve
  

.. _nodejs: https://nodejs.org/
.. _io.js: https://iojs.org/
.. _Python: https://www.python.org/downloads/release/python-2710/