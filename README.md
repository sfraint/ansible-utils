# Ansbile playbooks and utilities for Batfish

This repository contains utilities and example playbooks showing users how to use Batfish in conjunction with Ansible.


## Playbooks

### Setup

- **batfish_setup.yml**: Retrieves lastest Batfish docker image from DockerHub and installs the latest version of Pybatfish and other python dependencies. 

### Tutorials

- **bf_tutorial_1.yml**: The first Batfish tutorial, showing you how to retrieve facts about network devices

- **bf_tutorial_2.yml**: The second Batfish tutorial, showing you how to validate facts about network devices


## Pre-requisites
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

- **Setup Batfish**

  `ansible-playbook -i inventory playbooks/batfish_setup.yml`

- **Run the first Batfish tutorial**

  `ansible-playbook -i inventory playbooks/bf_tutorial_1.yml`

