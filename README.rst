========
Diaspora
========
Install a Diaspora pod on a single machine. 

Can be used to modify and deploy configuration files in ``/templates``. When modified they trigger restart of appropriate services.

Not suitable for Diaspora's upgrades.

Example
=======
First of all put certificates files (.crt ank .key) in role's `files` dir **or your production installation wont't work!**

Than create a playbook with these lines::

        - hosts: diaspora-pods 
          roles:
          - diaspora

Varialble ``diaspora_url`` must be specified per host. Easiest place to do so is in inventory file::

        [diaspora-pods]
        targetmachine1.net diaspora_url=pod.ofmine.tld
        targetmachine2.net diaspora_url=anotherpod.ofmine.tld

Variables
=========
- diaspora_version

Git tag of version to install. Default master.

- diaspora_url

This should be the URL you want to use to access the pod. Do not prepone ``http://`` nor postpone ``/`` to uri.
DO NOT CHANGE THIS AFTER INITIAL SETUP! *If you do change the URL, you will have to start again as the URL will be hardcoded into the database.*

Help & issues
=============
Please report bugs or feature request to improve this role.
