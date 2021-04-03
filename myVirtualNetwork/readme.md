## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Diagrams/networkDiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

Ansible/Jump-Box-Provisioner/
  - ansible.cfg
  - filebeat-config.yml
  - filebeat-playbook.yml
  - hosts
  - install-elk.yml
  - pentest.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box-Provisioner | Gateway  | 51.141.164.20 | Linux (Ubuntu) |
| Web-1    | DVWA Host | 52.191.187.94 | Linux (Ubuntu) |
| Web-2    | DVWA Host | 52.191.187.94 | Linux (Ubuntu) |
| theFirstElkMachine | Monitor | 168.61.172.150 | Linux (Ubuntu) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner can accept connections from the Internet. Access to this machine is only allowed from my personal IP address.

Machines within the network can only be accessed by the jump box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes     |    My IP address     |
| Web-1    |         No          | The jump box 10.0.0.11 |
| Web-2    |         No          | The jump box 10.0.0.11 |
| theFirstElkMachine | No        | The jump box 10.0.0.11 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is easy to replicate.

The playbook implements the following tasks:
- Installs docker.io and the docker module
- Installs python3
- Increases virtual memory
- Downloads and launches the docker container
- Ensures that docker starts on boot and restarts

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Diagrams/docker_ps

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.13
- Web-2 10.0.0.14

Filebeat has been installed on these machines.

Filebeat allows us to collect the following information from each machine:
- Filebeat collects log data which we can examine in kibana

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned (such the jump box): 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible/
- Update the hosts file to include the group for your elk machine and its ip address.
- Run the playbook, and navigate to your elk machine= to check that the installation worked as expected.
