## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 ![PJ1 drawio](https://user-images.githubusercontent.com/94761746/197031127-cf80b9e5-44e3-4b5f-8e97-d051dd3f6d86.png)

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

![PJdocker](https://user-images.githubusercontent.com/94761746/169676201-6c1c6982-0e47-4ec9-8253-a9f7936935cf.PNG)


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

Answer the following questions to fill in the blanks:

Which file is the playbook? Where do you copy it?

/etc/ansible/file/filebeat-config.yml

 Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Edit the etc/ansible/hosts file to add webserver/elkserver IP Address
 
Which URL do you navigate to in order to check that the ELK server is running? http://13.70.131.137:5601/app/kibana

![Kibana-elk-server](https://user-images.githubusercontent.com/94761746/169677167-ad738772-115c-43f2-966b-d8862b3d75ad.PNG)

Using the filebeat-playbook.yml

•	Create a new playbook in the /etc/ansible/roles/ directory that will install, drop in the updated configuration file, enable and configure system module, run the filebeat setup, and start the filebeat service.

•	Create a new playbook in the /etc/ansible/roles/ directory that will install, drop in the updated configuration file, enable and configure system module, run the metricbeat setup, and start the metricbeat service.

•	Run the playbooks, and navigate back to the installation page on the ELk-Server GUI, click the check data on the Module Status

•	Click the verify incoming Data to check and see the receiving logs from the DVWA machines.

you should see the following:

![Filebeat System log](https://user-images.githubusercontent.com/94761746/169677310-1d1be944-c715-4615-a792-ca7238fbdfcc.PNG)

Commands to run Ansible configuration for Elk-Server are:

ssh sysadmin@(jumpbox public IP)

sudo docker conatiner list -a

sudo docker start (name of container)

sudo docker attach (name of container)
