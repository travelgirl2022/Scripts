# Scripts
Linux Scripts and Ansible Scripts from my CyberClass
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Red Team Diagram] 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Filebeat.

•	ansible/install-elk.yml

This document contains the following details:
•	Description of the Topologu
•	Access Policies
•	ELK Configuration
o	Filebeats and Metricbeats installed
o	Web-1, Web-2 and Web-3 
•	How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
•	The load balancer is used to manage and enforce session ID’s in client cookies, as well as eliminates the use of web servers being observed outside the internal virtual network.
•	The jumpbox allows external access without having internal access to other resources. The only exception is when the jumpbox is attached to the docker container. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the web servers and system usage in Kibana dashboards included with each beats installation.
•	Filebeats locates and forwards log file data for analysis and review
•	Metricbeats locates and forwards metric data for analysis and review

The configuration details of each machine may be found below.

| **Name**             | **Function** | **Private IP** | **Public IP** | **Operating System** |
|----------------------|--------------|----------------|---------------|----------------------|
| Jump Box Provisioner | Gateway      | 10.0.0.4       | 104.43.192.13 | Ubuntu LTS 18.04     |
| Web-1                | Gateway      | 10.0.0.7       | 40.77.61.62   | Ubuntu LTS 18.04     |
| Web-2                | Gateway      | 10.0.0.8       | 40.77.61.62   | Ubuntu LTS 18.04     |
| Web-3                | Gateway      | 10.0.0.6       | 40.77.61.62   | Ubuntu LTS 18.04     |
| Elk Server           | Gateway      | 10.2.0.4       | N/A           | Ubuntu LTS 18.04     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box Provisioner and Elk-Server machines can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My IP 75.1.108.152

Machines within the network can only be accessed by Jump-Box Provisioner.

A summary of the access policies in place can be found in the table below.

| **Name**             | **Publicly Accessible** | **Allowed IP Addresses** |
|----------------------|-------------------------|--------------------------|
| Jump Box Provisioner | Yes                     | 75.1.108.152             |
| Web-1                | No                      | 10.0.0.7                 |
| Web-2                | No                      | 10.0.0.8                 |
| Web-3                | No                      | 10.0.0.6                 |
| Elk Server           | Yes                     | 75.1.108.152             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
•	It allows consistent and automatic setup

The playbook implements the following tasks:
•	Install Docker, Docker.io,and python3-pip packages with apt module
Run Elk docker container
•	Open specific TCP ports

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
•	Web-1: 10.0.0.7
•	Web-2: 10.0.0.8
•	Web-2: 10.0.0.6

We have installed the following Beats on these machines:
•	Filebeat
•	Metricbeat

These Beats allow us to collect the following information from each machine:
•	Filebeat passes & forwards system logs from VM’s to Elk Stack
•	Metricbeat reports system & service statistics about VM’s to the Elk Stack

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 


SSH into the control node and follow the steps below:
•	Copy the elk-stack-playbook.yml file to /etc/ansible/roles/
o	$ sudo docker cp elk-stack-playbook.yml <container.name>:/etc/ansible/roles/elk-stack-playbook.yml

•	Update the /etc/ansible/hosts file to include the Elk stack VM IP address
•	Run the playbook, and navigate to http://[your.elk.ip]:5601/app/kibana to check that the installation worked as expected.
o	$ ansible-playbook /etc/ansible/roles/elk-stack-playbook.yml

 


•	Edit /etc/ansible/files/filebeat-config.yml in the ansible container on the control node to include the ELK Stack IP address. You should also change the default login credentials.
•	Run the playbook
o	$ ansible-playbook /etc/ansible/roles/filebeat-playbook.yml

•	http://[your.elk.ip]:5601/app/kibana.
 
