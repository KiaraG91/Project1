## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 ![image](https://user-images.githubusercontent.com/94761746/169676049-51b16ad0-01b0-4e78-8a02-1b22e6c237e6.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

 Enter the playbook file

•	filebeat-playbook.yml
•	metricbeat-playbook.yml

This document contains the following details:
o	Description of the Topology
o	Access Policies
o	ELK Configuration
o	Beats in Use
o	Machines Being Monitored
o	How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

What aspect of security do load balancers protect? 
•	Load balancer protects the system from DDoS attacks by shifting attack traffic.
•	Load Balancing contributes to the availability aspect of security in regard to the CIA Triad.

What is the advantage of a jump box?
•	The jump box gives access to the user from a single node that can be secured and monitored.
•	The jump box is the origination point for launching the Administrative Tasks. This ultimately sets the jump box as a SAW (secure admin workstation). All Administrators when conducting any Administrative Task will be required to connect to the jump box (SAW) before performing any task or assignment.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

What does Filebeat watch for?
•	Filebeat watches for any information in the file system which has been changed and when it has.
•	Filebeat watches for log files/location and collects log events.

What does Metricbeat record?
•	Metricbeat takes the metrics and statistics that collects and ships them to the output you specify.
•	Metricbeat records metric and statistical data from the operating system and from services running on the server.


The configuration details of each machine may be found below.
| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | NO                  | 10.0.0.4             |
| ELK-Server | NO                  | 10.2.0.5             |
| Web-1      | NO                  | 10.0.0.8             |
| Web-2      | NO                  | 10.0.0.7             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:20.213.137.44 Machines within the network can only be accessed by SSH from Jump Box.

A summary of the access policies in place can be found in the table below.
| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | NO                  | 10.0.0.4             |
| ELK-Server | NO                  | 10.2.0.5             |
| Web-1      | NO                  | 10.0.0.8             |
| Web-2      | NO                  | 10.0.0.7             |


### Elk Configuration

Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible easily configures new machines, updates programs, and configurations on hundreds of servers at once, also the process is the same no matter if managing hundreds of machines or just one machine.

What is the main advantage of automating configuration with Ansible?
•	This allows you to deploy to multiple servers using a single playbook.

The playbook implements the following tasks:
•	Install docker.io
•	Install Python-pip
•	Install docker container
•	Launch docker container: elk
•	Command: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

•	Web-1 (DVWA 1)   10.0.0.8
•	Web-2 (DVWA 2) 10.0.0.7

I have installed the following Beats on these machines:
•	Filebeat
•	Metricebeat


These Beats allow us to collect the following information from each machine:
•	Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
•	Metricbeat collects metrics from the operating system and from services running on the server.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible
- Update the configuration file to include the webservers and ElkVM
- Run the playbook and navigate to ElkVM to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
