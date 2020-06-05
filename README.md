# Virtual-Network
This is to show how I created my Azure virtual network, and deployed ansible container and also installed ELK Stack to monitor my VM's 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Azure Virtual Network.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

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

Load balancing ensures that the application will be highly ___responsive__, in addition to restricting _overload____ to the network.
: What aspect of security do load balancers protect? DDOS and Information security (Data) 
What is the advantage of a jump box?_
Jump Box is the only VM in Azure to enable connectivity over the internet. Jump Box prevents all Azure VM’s to expose to the public. We can do monitoring and logging on a single box. We can easily turn the ON/OFF remote desktop connectivity feature. By using the network security group, we can restrict the IP addresses to communicate with the Jump Box. We can block the public IP associated with the VM, it helps to improve security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the ___log management__ and system _____.
What does Filebeat watch for?_Log files (Log data)
What does Metricbeat record?_ Metrics from 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.8   | Linux            |
| -Elk     |          |            |                  |
| DVWA-VM1     | LB     | 10.0.0.5    | Linux        |
| DVWA-VM2     | LB     | 10.0.0.7    | Linux        |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _JumpBox-Elk____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
75.5.174.209

Machines within the network can only be accessed by __JumpBox-Elk___.
JumpBox-Elk Which machine did you allow to access your ELK VM? What was its IP address?_ 10.0.08

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.5 10.0.0.7    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time and less vulnerable to error.
What is the main advantage of automating configuration with Ansible?_
Difficult manual tasks become repeatable and less vulnerable to error

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Disable firewall or open ports
- Download Image
- Install java
- install Elasticsearch
- Install Kibana
-Install Logstach

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring_
10.0.0.5, 10.0.0.7

We have installed the following Beats on these machines: Filebeat and Metricbeat


These Beats allow us to collect the following information from each machine:
Filebeat ships log files. It generate log files, tailing them and forwarding the data either Logstash for more processing or directly into Elasticsearch for indexing.
Metricbeat monitors and collects metrics from the system and services running on the server. It allows you to monitor for errors and see debug messages to diagnose what went wrong.
### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the __Elk config___ file to __hosts file___.
- Update the _hosts____ file to include the IP addreses of VM’s, webservers 
- Run the playbook, and navigate to _Elk server___ to check that the installation worked as expected.

: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? ELK config Where do you copy it?_Hosts 
- _Which file do you update to make Ansible run the playbook on a specific machine? Hosts file
 How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ ssh to ansible on the machine you want to install ELK on and then install it. For filebeat, Elk must have been installed and running to be able to install filebeat
- _Which URL do you navigate to in order to check that the ELK server is running? LocalIP:5601

