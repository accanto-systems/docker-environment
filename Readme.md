# Vagrant Docker Location

Vagrantfile for a pair of docker locations

## Pre-requisites
For a Vagrant install, the following software must be installed on your host machine.
* [Vagrant](https://www.vagrantup.com/)
* [Virtualbox](https://www.virtualbox.org/) (support for libvirt is also provided in the Vagrantfile)

To install on an existing server you need to install the following on your host machine.
* [Ansible](https://www.ansible.com/)

## Run the Vagrant box

To create a docker environment, run the following commands on your machine

```
cd docker-location
vagrant up
```

## Run Ansible playbooks

To create a docker location on an existing server, you can update the variables in **docker-location/variables.yml** and run the following command from a shell prompt.

```
ansible-playbook --inventory-file=inventory.yml start-dockerlocation.yml
```

Update **docker-location/inventory.yml** with your target server details.

### Configure your vagrant box

The following configurable options are available in the Vagrantfile. Comment/uncomment the appropriate lines to enable/disable the following options.

| Option             | Description                               | Default                                              |
|--------------------|-------------------------------------------|------------------------------------------------------|
| aioip              | IP address of AIO ALM instance            |                                                      |
| armip              | IP address of Ansible RM                  | Yes                                                  |
| registries         | comma seperated list of insecure regitries| 'lifecyclemanager.com:5001,lifecyclemanager.com:5002'|

### Accessing the environment

When the installation is finished you can access the following services

|**AIO Services**| Address                                                   |
|----------------|-----------------------------------------------------------|
|**Portainer**   | http://192.168.56.110:9000                                |
