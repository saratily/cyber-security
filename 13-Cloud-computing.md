# Week 13: Introduction to Cloud Computing

- [Week 13: Introduction to Cloud Computing](#week-13--introduction-to-cloud-computing)
  * [SUMMARY:](#summary-)
  * [DAY-1](#day-1)
    + [1. Resource Group - RedTeam](#1-resource-group---redteam)
    + [2. Virtual Network - RedTeamNet](#2-virtual-network---redteamnet)
    + [3. Network Security Group - RedTeamSG](#3-network-security-group---redteamsg)
      - [SG Inbound rules](#sg-inbound-rules)
    + [4. VMs](#4-vms)
  * [DAY-2](#day-2)
    + [Commands](#commands)
    + [1. Network Security Group - RedTeamSG](#1-network-security-group---redteamsg)
      - [Add SG Inbound rules](#add-sg-inbound-rules)
    + [2, Changes in Virtual Machines](#2--changes-in-virtual-machines)
  * [DAY 3](#day-3)
    + [Ansible script](#ansible-script)
    + [1. Load Balancer - RedTeamLB](#1-load-balancer---redteamlb)
      - [Frontend IP config](#frontend-ip-config)
      - [Backend pool](#backend-pool)
    + [2. Network Security Group - RedTeamSG](#2-network-security-group---redteamsg)
      - [Add SG Inbound rules](#add-sg-inbound-rules-1)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>


## SUMMARY:
```
Local Workstation   -> 73.70.75.51
JUMP-BOX -> 20.150.146.59 / 10.0.0.4 (7)
Web-1   -> 10.0.0.5      
Web-2   -> 10.0.0.6
Web-3   -> 10.0.0.7
LB      -> 20.163.98.9

VNet -> 10.1.0.0/16
Subnet -> default 10.1.0.0/24

ssh form local to Jump-Box: ssh azureuser@20.150.146.59
ssh from Jump-Box to Web-1: ssh azureuser@10.0.0.5

curl inside Web-1: curl http://localhost/setup.php
LB -> browser: http://20.163.98.9/setup.php
```

## DAY-1
### 1. Resource Group - RedTeam

| Subscription         | Resource Group | Region    |
|----------------------|----------------|-----------|
| Azure Subscription 1 | RedTeam        | US West 3 |

### 2. Virtual Network - RedTeamNet

| Subscription         | Resource Group | Name       | Region    | Address space | Subnet |
|----------------------|----------------|----------- |-----------|--------------|----|
| Azure Subscription 1 | RedTeam        | RedTeamNet | US West 3 | 10.1.0.0/16 | default 10.1.0.0/24 |   

### 3. Network Security Group - RedTeamSG

| Subscription         | Resource Group | Name       | Region    |
|----------------------|----------------|----------- |-----------|
| Azure Subscription 1 | RedTeam        | RedTeamSG | US West 3  |

#### SG Inbound rules

| Rule     | src:port       | dest:port | Service | Protocol | Action | Priority |
|----------|----------------|-----------|---------|----------|--------|----------|
|ALlow RDP | My IP Address:*| Any:3389     | RDP     | TCP      | Allow  | 100      |
|Deny Any  | Any:*          | Any: *       | Custom  | Any      | Deny   | 4096     |

### 4. VMs
|                   | Jump-Box              | Web-1                 | Web-2                             |
| ----------------- | --------------------- | --------------------- | --- |
|Subscription       | AzureSubscription 1   | AzureSubscription 1   | AzureSubscription 1 |
|Resource Group     | RedTeam               | RedTeam               | RedTeam                           |
|SSH key            | local SSH             | local SSH             | local SSH                         |
|Region             | US West 3             | US West 3             | US West 3                         |
|Availability set   | None                  | Web-AV                | Web-AV                            |
| RAM               | 1 GB                  | 2 GB                  | 2 GB                              |
|vCPU               | 1                     | 1                     | 1                                 |
|Security Group     | RedTeamSG             | RedTeamSG             | RedTeamSG                         |
|Vnet               | RedTeamNet            | RedTeamNet            | RedTeamNet                        |
        
## DAY-2

### Commands
```
# For new machines, update apt
azureuser@Jump-Box-Provisioner:~$ sudo apt update

# Install docker
azureuser@Jump-Box-Provisioner:~$ sudo apt-get install docker.io

# Check docker status
azureuser@Jump-Box-Provisioner:~$ sudo systemctl status docker

# Pull cyberxsecurity/ansible container
azureuser@Jump-Box-Provisioner:~$ sudo docker pull cyberxsecurity/ansible

# Go inside docker container - RUN THIS CMD ONLY ONCE - OTHERWISE IT WILL CREATE MULTIPLE CONTAINER - AND MAKE THINGS COMPLICATED
azureuser@Jump-Box-Provisioner:~$ sudo docker run -ti cyberxsecurity/ansible:latest

# List all containers
azureuser@Jump-Box-Provisioner:~$ sudo docker container list -a

# Start a container by its name ie.e charming_knuth
azureuser@Jump-Box-Provisioner:~$ sudo docker start charming_knuth
charming_knuth

# Launch the container
azureuser@Jump-Box-Provisioner:~$ sudo docker attach charming_knuth

# Generate ssh key in Jump-Box
root@c6af0046116f:~# ssh-keygen

# ssh into Web-1 and Web-2 from Jump-Box
root@c6af0046116f:~/.ssh# ssh azureuser@10.0.0.5
root@c6af0046116f:~/.ssh# ssh azureuser@10.0.0.6

# Update hosts and ansible.cfg with Web-1 and Web-2
root@c6af0046116f:~# cd etc/ansible/

root@c6af0046116f:~# ls
ansible.cfg     hosts

root@c6af0046116f:/etc/ansible# nano hosts 
# uncomment [webservers] 

# Add
10.0.0.5 ansible_python_interpreter=/usr/bin/python3
10.0.0.6 ansible_python_interpreter=/usr/bin/python3  

root@c6af0046116f:/etc/ansible# nano ansible.cfg
# Ctrl + w -> for search, search for remote_user add azureuser as remote_user
#remote_user = root
remote_user = azureuser     ----> Add

# Test an Ansible connection all -m ping

root@c6af0046116f:/etc/ansible# ansible

```
### 1. Network Security Group - RedTeamSG
#### Add SG Inbound rules

| Rule     | src:port       | dest:port | Service | Protocol | Action | Priority |
|----------|----------------|-----------|---------|----------|--------|----------|
|Allow SSH | My IP Address:*| ServiceTag:22| SSH     | TCP      | Allow  | 200      |
||| Virtual Network|||| 
| Cidr SSH | IP addresses:* | ServiceTag:22| SSH     | TCP      | Allow  | 150 |
|| 10.0.0.4:* | Virtual Network ||||


### 2, Changes in Virtual Machines

|           | Jump-Box               | Web-1         | Web-2        |
| --------- | -----------------------| ------------- | -------------|
| SSH key   | local SSH              | jump-box SSH  | jump-box SSH |
| docker    | docker.io              |||
| ansible   | cyberxsecurity/ansible |||


## DAY 3

### Ansible script
```
- name: My first playbook
  hosts: webservers
  become: true
  tasks:
    - name: Install apache httpd (state=present is optional
      apt:
        name: apache2
        state: absent
```

### 1. Load Balancer - RedTeamLB
| Subscription         | Resource Group | Name      | Region    | SKU    |Type    |Tier    |
|----------------------|----------------|-----------|-----------|--------|--------|----------|
| Azure Subscription 1 | RedTeam        | RedTeamLB | US West 3  | Basic | Public | Regional |

#### Frontend IP config
| Name       | IP version | Public IP address |
| ---------- |------------|-------------------|
|RedTeamLBF  | IPv4       | Create New |
||| Name: RedTeamLBF |
|||SKU: Basic |
||| Tier: Regional |
||| Assignment: Static |

#### Backend pool
| Name         | Virtual Machines |
|--------------|------------------|
|RedTeamLBpool | Web-1            |
|              | Web-2            |
Note: Several fields will be inherited from Web-1 and Web-2

### 2. Network Security Group - RedTeamSG
#### Add SG Inbound rules

| Rule     | src:port        | dest:port   | Service | Protocol | Action | Priority|
|----------|-----------------|-------------|---------|----------|--------|---------|
|Allow HTTP | My IP Address:*| ServiceTag:80| HTTP   | TCP      | Allow  | 300     |
||| Virtual Network|||| 

- Remove Deny any rule which was created on Day 1

