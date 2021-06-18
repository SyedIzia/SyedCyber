## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<a href="https://github.com/SyedIzia/SyedCyber/blob/main/Diagrams/VM_Network%20Diagram.png">Virtual Machine Diagram</a>

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

[Ansible_Playbook_Files](https://github.com/SyedIzia/SyedCyber/tree/main/Ansible)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.

- Load balancers protects the system from DDoS attacks by shifting attack traffic. The advantage of a jump box is to give access to the user from a single node that can be        secured and monitored. If only the jump box is allowed to connect to machines behind a netwrok security group, that is only one point to protect rather than exposing multiple points to attackers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server and system files.
- Filebeat ships log files from specified locations and forwards them to the ELK stack.
- Metricbeat monitors traffic on your servers (CPU, Memory Usage, Disk Space used) by container.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | VM       | 10.0.0.5   | Linux            |
| Web-2    | VM       | 10.0.0.6   | Linux            |
| ELK-VM   | VM       | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 76.30.95.235

Machines within the network can only be accessed by Jump Box.
- Machine allowed to access your ELK VM is JumpBoxProvisioner and the IP address is 10.0.04

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4             |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The primary benefit of Ansible is it allows IT administrators to automate away the drudgery from their daily tasks. That frees them to focus on efforts that help deliver more value to the business by spending time on more important tasks.

The playbook implements the following tasks:
- Install Docker
- Install Pip3
- Checks on memory space
- Downloads and launches the Elk Docker Container



The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:

- Filebeats collect log data and changes made for the VMs. Filebeats can show IPs from inbound traffic, Geolocation, Requests being made, etc.
- Metricbeats collects activity and status of the connected VMs. Here you can see CPU, memory usage, number of containers, etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible file to etc/ansible.
- Update the hosts file to include webservers ip addresses and webservers group
- Run the playbook, and navigate to Virtual Machine to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Ansible Playbook Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
