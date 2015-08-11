# subunit2sql-vagrant

## Pre-requisites
In order to run this environment you will need Vagrant, Virtualbox, Python and Ansible installed.

For instance to install Ansible you need to run the following pip command:

	pip install ansible

## How to use
Just go to the root directory of this project and run:

	vagrant up
   
This should trigger the machine setup and provisioning, if for some reason the provisioning does not execute, run the following command to force it:
	
    vagrant provision

This will provision the machine using Ansible and run all its rules for the Vagrant VM. After that you can access the MySQL `openstack` database with the subunit2sql schema.

The connection URL for this database is `mysql://vagrant:vagrant@127.0.0.1/openstack`

To populate your database with some tests you can pipe any subunit output to `subunit2sql`:

    source ~/.venvs/subunit2sql/bin/activate
    MYCONN=mysql://vagrant:vagrant@127.0.0.1/openstack
    cat [all_my_tests.subunit] | subunit2sql --database-connection $MYCONN
