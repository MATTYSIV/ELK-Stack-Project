## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
![diagram ](https://user-images.githubusercontent.com/106646100/173477113-9c7c2393-212f-4693-a7c4-1d2f6de401fa.png)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

   - [install-elk.yml](https://github.com/MATTYSIV/ELK-Stack-Project/blob/main/Ansible/install-elk.yml)
   - [Filebeat-config.yml](https://github.com/MATTYSIV/ELK-Stack-Project/blob/main/Ansible/filebeat-config.yml)
   - [Filebeat-Playbook.Yml](https://github.com/MATTYSIV/ELK-Stack-Project/blob/main/Ansible/filebeat-playbook.yml)
   - [Metricbeat-config.yml](https://github.com/MATTYSIV/ELK-Stack-Project/blob/main/Ansible/metricbeat-config.yml)
   - [Metricbeat-playbook.yml](https://github.com/MATTYSIV/ELK-Stack-Project/blob/main/Ansible/metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly functional,in addition to restricting high-traffic to the network.

  Main purpose is to distribute web traffic across multiple server

  It helps prevent overloading servers as well as optimizes productivity
  It protect critical web applications
  It allows high avalibility.protecting against attack such as distributed denial-of=service (DDOS) attack
  
  What is the advantage of a jump box?
  It is a gateway on a network use to manage devices in different security zones
  It helps to improve security and it is also prevents all azure VM to expose to public

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network

- What does Filebeat watch for?_
- It monitors the log files 
- What does Metricbeat record?_
  Metricbeat helps monitor servers by collecting metric from the system and services running  
The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.5   | Linux            |
| Web -1   | DVWA     | 10.0.0.4   | Linux            |
| Web -2   | DVWA     | 10.0.0.6   | Linux            |
| ELK-VM   |ELK-Server| 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump  Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My home network public IP address

Machines within the network can only be accessed by JumpBox
- JumpBox machine allowed SSH to access your ELK VM .Jump Box IP address is 20.92.74.148

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.5             |
| Web-1    | NO                  | 10.0.0.4             |
| Web-2    | NO                  | 10.0.0.6             |
|ELK-VM    | NO                  | 10.2.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because 
it allows IT administrators to automate their everyday task.
-  What is the main advantage of automating configuration with Ansible?_
-  It is an opensource tool for IT configuration management,deployment,Organizations could massive improvements in productivity
-  by resolving various automation challenges

The playbook implements the following tasks:
- _ In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
    - .Intially SSH into Jump-Box-Provisioner
    - ..Run docker container list -a it is to verify that the container is on and then start/Attached to the ansible docker.
    - And then went to /eic/ansible/roles directory and created the ELK playbook.
    - Run the ELK-playbook.yml
    - Finally SSH into the ELK-VM to verify the server is up and running.                                                                                                                                                               
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  
![docker_ps_output png](https://user-images.githubusercontent.com/106646100/174461039-ff5fa2ca-d94f-44ac-ac2d-e9bf24c80d22.png)

(### Target Machines & Beat
This ELK server is configured to monitor the following machines:
-  Web-1 10.0.0.4
-  Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files that collects log events and forwards them to Elasticsearch or logstash
- Metricbeat records metrics and statistical data from the operating system metrics such as CPU or memory or data related to services running on the server. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the configutation files such as ELK,filebeat,Metricbeat to /etc/ansible/files/
- Copy the Playbook YAML of filebeat and Metricbeat to /etc/ansible/roles.
- Update the /etc/ansible/hosts file to include  the Webservers and the ELK server
- Run the ansible playbook install_elk.yml,filebeat_playbook.yml and metricbeat_playbook.yml 
- Navigate to http://20.227.128.40:5601/app/kibana to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
