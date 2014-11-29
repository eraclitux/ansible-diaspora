================
Ansible Diaspora
================
Ansible role to install and configure a Diaspora pod on a single machine. 

Can be used to modify and deploy configuration files in ``/templates``. When modified they trigger restart of appropriate services.

Not suitable for Diaspora's upgrades.

Example
=======
First of all put certificates files (.crt ank .key) in role's ``files`` dir **or your production installation wont't work!**

Than create a playbook with these lines::

        - hosts: diaspora-pods 
          roles:
          - diaspora

Varialble ``diaspora_url`` must be specified per host. Easiest place to do so is in inventory file::

        [diaspora-pods]
        targetmachine1.net diaspora_url=pod.ofmine.tld
        targetmachine2.net diaspora_url=anotherpod.ofmine.tld

Now installing Diaspora is as easy as running (better in ``screen`` as it takes time)::

        ansible-playbook diaspora.yml

After installation is finished login to remote server and issue::

        sudo -i -u diaspora 
        ./diaspora/script/server

Variables
=========
- diaspora_version

Git tag of version to install. Default master.

- diaspora_url

This should be the URL you want to use to access the pod. Do not prepone ``http://`` nor postpone ``/`` to uri.
DO NOT CHANGE THIS AFTER INITIAL SETUP! *If you do change the URL, you will have to start again as the URL will be hardcoded into the database.*

SSL cerificate
==============
Get for free a certificate from startssl.com and follow `these instructions <http://www.startssl.com/?app=42>`_ to create required files and put them into ``files`` folder. They *must* be named ``diaspora_cert.crt`` and ``diaspora_cert.key``. This is required for a production installation.

Help & issues
=============
Please `report bugs or feature requests <https://github.com/eraclitux/ansible-diaspora/issues>`_ to improve this role.
