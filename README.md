# ELK_Stack_Project
ELK Stack Project
## Automated ELK Stack Deployment


The files in this repository were used to configure the network depicted below.


(README/Images/AzureCloudDiagram.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.


  - filebeat-playbook.yml


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build
### Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Furthermore, the load balancers ensure availability of services by distributing network traffic across the server behind it. It will help minimize the effects of DDoS attacks. The jumpbox acts as a gateway to the configuration environment. It provides a single location of configuration files and other resources used to deploy the ELK stack.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
Filebeat will monitor the changes to the files on the server and metricbeat will provide information about system resources and performances.
The configuration details of each machine may be found below.
| Name     | Function | IP Address | Operating System  |
|----------|----------|------------|-------------------|
| Jump Box | Gateway  | 10.0.0.4   |Linux (Ubuntu 20.04|
| Web-1    | Webserver| 10.0.0.5   |Linux (Ubuntu 20.04|
| Web-2    | Webserver| 10.0.0.6   |Linux (Ubuntu 20.04) |
| ELKvm    | Logserver| 10.1.0.4   |Linux (Ubuntu 20.04) |
### Access Policies
The machines on the internal network are not exposed to the public Internet. 
Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-  Local IP: 142.129.168.120
 
Machines within the network can only be accessed by Jumpbox.
- Only the Jumpbox has access to the ELKvm via port 22
- Only the host machine with the public IP of 142.1219.168.120 on port 5602 with a web browser.
A summary of the access policies in place can be found in the table below.
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 142.129.168.120:22   |
| Web-1    | No                  | 10.0.0.5:22          |
| Web-2    | No                  | 10.0.0.6:22          |
| ELKvm    | No                  | 142.129.168.120:5602 |
### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Configuration as code allows for easy deployment and re-deployment with the same configuration reducing human error. It makes it easier
The playbook implements the following tasks: 
- Install Docker, Pip3, docker python module
- Increased VM memory allocation
- Download then installs ELK container and maps port 5601 to 5601 and 9200 to 9200
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
 (README/Images/ElkDockerPS.png) 
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5
Web-2 10.0.0.6
We have installed the following Beats on these machines:
Filebeat version 7.4.0
Metricbeat version 7.4.0
These Beats allow us to collect the following information from each machine:

Filebeat monitors and collects the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat monitors and collects system-level CPU usage, memory, file system, disk IO, and network IO statistics, as well as top-like statistics for ever process running on your machine. 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml to /etc/ansible/files/Filebeat-config.yml.
- Update the filebeat-config.yml file to include
  - Username and password
  - Host IP and port for ELKvm
- Run the playbook, and navigate to the http://20.114.236.27:5601/ to check that the installation worked as expected.
  - Navigate to the Filebeat installation and Metricbeat installation page on the ELK server GUI.
  - Verify that step 5: Module Status and click Check Data.
- Filebeat-playbook.yml is the playbook. Copy it to /etc/ansible/roles
- Update the hosts file to indicate which machine to install the ELK server.
- Navigate to http://20.114.236.27:5601/ in order to check that the ELK server is running.
