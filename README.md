## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk-Stack-Project/ElK-Stack-Scripts/filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name      | Function | IP Address | OS    |
|-----------|----------|------------|-------|
| JumpBox   | Gateway  | 10.0.0.4   | Linux |
| ElkServer | ELK      | 10.1.04    | Linux |
| Web1      | DVWA     | 10.0.0.5   | Linux |
| Web2      | DVWA     | 10.0.0.6   | Linux |
| Web3      | DVWA     | 10.0.0.7   | Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk Stack machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
  97.117.97.197


Machines within the network can only be accessed by the Jumpbox. The public IP address of the Jumpbox is 52.156.70.255.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.5
-10.0.0.6
-10.0.0.7

We have installed the following Beats on these machines:
-FileBeat
-MetricBeat

These Beats allow us to collect the following information from each machine:
-Filebeat allows us to monitor log files from each machine I decide to watch. It will also collect these events and send them to Elasticsearch or Logstach for deeper analysis.
- Metricbeat shows us the metrics and stats of our own servers. This sends data to Elasticsearch and Logstash for more detailed analysis. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the_____file to /etc/ansible.
- Update the _____ file to include...
- Run the playbook, and navigate to http//(elk public ip here)5601:/app/Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._