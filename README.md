# Ansbile playbooks and utilities for Batfish

This repository contains utilities and example playbooks showing users how to use Batfish in conjunction with Ansible.


## Playbooks

### Setup

- **batfish_setup.yml**: Retrieves latest Batfish docker image from DockerHub and installs the latest version of Pybatfish along with the other python module requirements. 

### Tutorials

- **bf_tutorial_1.yml**: Shows you how to retrieve facts about network devices

- **bf_tutorial_2.yml**: Shows you how to validate facts about network devices

- **bf_tutorial_3.yml**: Shows you how to validate the routing and forwarding behavior of the network

- **bf_tutorial_4.yml**: Shows you how to validate the behavior of a packet filter(ACL/Firewall rule) 

- **bf_tutorial_5.yml**: Shows you how to validate configuration attributes to find mis-configured BGP sessions and undefined references

## Pre-requisites
- Docker must be installed and running on your machine

- Install the [Batfish role](https://galaxy.ansible.com/batfish/base) from Ansible Galaxy 

- In the directory where you clone this repository, you must create a `data/bf_facts` folder. This folder is where the `bf_tutorial_1.yml` playbook will create individual fact files for each device in the example network

- If you are using a Python virtual environment and are running Ansible within that environment, you will need to ensure that the following lines appear in either your `inventory` 
```
  [localhost]
  ansible_connection=local
  localhost ansible_python_interpreter=python
```

or these lines appear in your `ansible.cfg` file. For a more detailed example of this file, follow this [link](https://raw.githubusercontent.com/ansible/ansible/devel/examples/ansible.cfg)

```
  [inventory]
  localhost ansible_python_interpreter=python
```


## Playbook invocation

- **Setup Batfish on your local machine**

  This playbook will download the latest Batfish docker container, Pybatfish SDK and other Python requirements and install it on your local machine. It always runs on `localhost`

  The playbook has some rudimentary error checking built into it:  
  - Aborts if Docker is not running.
  - Warns if it does not detect a Python virtual environment and ask you to confirm that you want to proceed with the installation
  
  `ansible-playbook -i inventory playbooks/batfish_setup.yml`

- **Run your first Batfish tutorial**

   Batfish is designed to provide complete network analysis, which is why all Batfish related modules should always to delegated to `localhost` and set to run once.
   This playbook is setup that way, so you can incorporate non-Batfish tasks that need to run across other hosts in your inventory

  `ansible-playbook -i inventory playbooks/bf_tutorial_1.yml`

   Each playbook is a standalone tutorial, it does not depend on any playbooks having been run first. So feel free to execute them in whatever order you think is best.
