## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Files and system metrics.

Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash

The configuration details of each machine may be found below.


| Name          | Function       | IP Address    | Operating System    | 
|------         |----------      |------------   |------------------   |
| Jump Box      | Gateway        | 10.0.0.4      | Linux               |  
| Admin WS      | User Interface | Source IP     | User's Determination   
| Load Balancer | Redunancy      | 20.150.138.13 | Azure               |  
| ELK Server    | SIEM           | 10.1.0.5      | Linux               |  
| WEB 1         | DVWA Container | 10.0.0.5      | Linux               |  
| WEB 2         | DVWA Container | 10.0.0.6      | Linux               |  
| WEB 3         | DVWA Container | 10.0.0.7      | Linux               |  
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
192.168.0.30


Machines within the network can only be accessed by other machines in the same network. 


A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Address |
| Jump Box      | Yes                 | 192.168.0.30 |
| Load Balancer | Yes                 | 192.168.0.30|
| ELK Server    | no                  | 10.1.0.5 13.68.246.109 |
| WEB 1         | no                  | 10.0.0.5 |
| WEB 2         | no                  | 10.0.0.6 |
| WEB 3         | no                  | 10.0.0.7 |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible is an easy to use programing language with the compatability to be used in multiple environments with excellent scaling.

The playbook implements the following tasks:
- Installs Docker and configures containers for use.
- the Containers will be set with installs of DVWA webmachines.
- Python is installed to allow for installation pip files.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:

WEB1-10.0.0.5 ; WEB2-10.0.0.6 ; WEB3-10.0.0.7 

We have installed the following Beats on these machines:
FileBeat and Metricbeat

These Beats allow us to collect the following information from each machine:
Metricbeat is used to track system metrics and statistics and sends the output to the ELK machine. An Example of what is logged with metricbeat are the cpu usage, memory usage and amount of disk space used. 

Filebeat is a lightweight shipper for forwarding and centralizing log data. Access and Error logs are just a fraction of the data filebeat consolidates into to ELK Machine. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Install-elk file to the Ansible Folder.
- Update the Ansible Host file to include Hostnames and IPs of the containers and the ELK server. 
- Run the playbook, and navigate to 10.1.0.5:5604(private ip of ELK Server and the port kibana works out of) to check that the installation worked as expected.

