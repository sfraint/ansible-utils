# Ansbile playbooks and utilities for Batfish

This repository contains utilities and example playbooks showing users how to use Batfish in conjunction with Ansible.


## Playbooks

- **batfish_setup.yml**: Retrieves lastest Batfish docker image from DockerHub and installs the latest version of Pybatfish and other python dependencies. 

- **bf_tutorial_1.yml**: The first Batfish tutorial, showing you how to retrieve facts about network devices


## Pre-requisites
- In the directory where you clone this repository, you must create a `data/bf_facts` folder. This folder is where the `bf_tutorial_1.yml` playbook will create individual fact files for each device in the example network

## Playbook invocation

- **Setup Batfish**

  `ansible-playbook -i inventory playbooks/batfish_setup.yml`

- **Run the first Batfish tutorial**

  `ansible-playbook -i inventory playbooks/bf_tutorial_1.yml`

