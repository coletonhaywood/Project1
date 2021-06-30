# Project1
Elk Stack Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/coletonhaywood/Project1/blob/8ef314b4aa86ddd764189ba44df0443ddbd485c1/Diagrams/ELK_Network_Diagram.PNG


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/coletonhaywood/Project1/blob/0aa0e56e85c5b7843afc4365fdf9a4802743aa5f/Ansible/filebeat-config.yml_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancing will help redue the efficiency of a DDoS attack by sharing the load of network traffic between three virtual machines. The advantage of the JumpBox is to prevent all of your virtual machines from direct access to the network, this creates a more secure network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- Filebeat collects data on the file system, which monitors which files have changed and when they were changed 
- Metricbeat collects machine metrics, such as uptime.

The configuration details of each machine may be found below.

| Name    | Function       | IP Address | Operating System |
|---------|----------------|------------|------------------|
| JumpBox | Gateway        | 10.1.0.4   | Linux            |
| Web-1   | DVWA Container | 10.1.0.5   | Linux            |
| Web-2   | DVWA Container | 10.1.0.6   | Linux            |
| Web-3   | DVWA Container | 10.1.0.8   | Linux            |
| ELK-VM  | Server         | 10.0.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 184.147.113.118

Machines within the network can only be accessed by JumpBox.
- The ELK-VM can only be accessed from the following virtual machines; Web-1, Web-2, Web-3, and the JumpBox.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses     |
|----------|---------------------|--------------------------|
| Jump Box | No                  | 187.147.113.118          |
| Web-1    | No                  |10.1.0.4/ 187.147.113.118 |
| Web-2    | No                  |10.1.0.4/ 187.147.113.118 |
| Web-3    | No                  |10.1.0.4/ 187.147.113.118 |
| ELK-VM   | No                  | 187.147.113.118          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it enables IT administrators the ability to automate your daily work tasks and give the administrator more time to focus on the needs of the business.

The playbook implements the following tasks:
- Configures ELK-VM with Docker.io
- Installs Docker.io
- Installs pip3
- Downloads and launches a docker elk container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/coletonhaywood/Project1/blob/8d2b3e253972629413bb74d7001740f1aca1851d/Diagrams/dockerps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.1.0.5
- Web-2 10.1.0.6
- Web-3 10.1.0.8

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects data about the file system, which files have changed and when they changed.
- Metricbeat collects machine metrics, such as uptime

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to ~/etc/ansible
- Update the ~/etc/ansible/hosts file to include host group, private IP addresses and python via "ansible_python_interpreter=/usr/bin/python3'
- Run the playbook, and navigate to 'curl localhost/setup.php to check that the installation worked as expected.
- The playbooks are install_elk.yml, filebeat-config.yml, metricbeat_config.yml, pentest.yml; all of these are copied in the /etc/ansible directory._
- To check if the ELK server is running, navigate to http://10.1.0.4:5601/app/kibana

Inorder to run and download the playbook and update the files the user will have to run the following code in a terminal with SSH connection to the Jumpbox, and inside the docker;

 $ ansible-playbook [name_of_playbook].yml

