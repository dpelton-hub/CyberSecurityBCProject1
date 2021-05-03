# CyberSecurityBCProject1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Diagrams/AxureNetworkDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook files may be used to install only certain pieces of it, such as Filebeat.

  - _ELK-INSTALL.YML_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundent, in addition to restricting access to the network.
-Using a load balancer ensures traffic is evenly distributed, preventing 1 server from being overloaded.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server and system logs.
- FileBeat keeps a state of each file it is monitoring and sends any changes made to those file
- MetricBeat collects information from your operating system

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| WebVM1   | Webserver| 10.0.0.8   | Linux            |
| WebVM2   | Webserver| 10.0.0.8   | Linux            |
| ELK      | ElkServer| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 63.155.39.126

Machines within the network can only be accessed by the Jump Box.
- Only my personal computer is able to access the Jump box at IP provided above,

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 137.135.48.126       |
| WebVM1   | No                  |                      |
| WebVM2   | NO                  |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- This ensures accuracy and speed during any future deployments.

The playbook implements the following tasks:
- Installs Docker 
- Installs Python3
- Installs ELK Stack

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Diagrams/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.8
- 10.0.0.9

We have installed the following Beats on these machines:
- FileBeats
- MetricBeats

These Beats allow us to collect the following information from each machine:
- Filebeats is used to collect information about any files being changed or modified on the server, incase of unauthorized access.
- MetricBeats is used to monitor the traffic to the web server, to have a better view of busy times and determine if a DDOS attack or other attacks are being ran on the web server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat-config.yml file to /etc/filebeat/filebeat.yml
- Update the Config file to include the host IP of your ELK stack machine and the ports needed to access Kibana
- Run the playbook, and navigate to LOCALHOST:5601 to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?_ Filebeat-Install.yml is the playbook to install and needs to be in /etc/ansible/roles directory
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ To run the playbook on multiple VM's you need to update the /etc/anisible/hosts file to include all the IP under the header [webservers]
- _Which URL do you navigate to in order to check that the ELK server is running?To verify the ELK servier is running naviagate to LOCALHOST:5601.
