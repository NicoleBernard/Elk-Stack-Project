## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(https://github.com/NicoleBernard/Elk-Stack-Project/blob/main/images/Elk_Stack_Diagram.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Elk-Stack-Project/ElK-Stack-Scripts/filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology 
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

A summary of the access policies in place can be found in the table below.
| Name      	| Publicly Accessible  	| Allowed IP Address                                  	|
|-----------	|----------------------	|-----------------------------------------------------	|
| JumpBox   	| Gateway through SSH  	| 10.0.0.4, 10.0.0.0/16, Personal IP,                 	|
| ElkServer 	| ELK                  	| 10.1.0.4, 10.0.0.4, Personal IP (port 80, Elk 5601) 	|
| Web1      	| DVWA                 	| 10.1.0.4, 10.0.0.4, Personal IP (port 80, Elk 5601) 	|
| Web2      	| DVWA                 	| 10.1.0.4, 10.0.0.4, Personal IP (port 80, Elk 5601) 	|
| Web3      	| DVWA                 	| 10.1.0.4, 10.0.0.4, Personal IP (port 80, Elk 5601) 	|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it can automate complex configurations on multipule virtual machines. Ansible allows for a playbook to be run. Where the automation is defined through using YAML format.


The playbook implements the following tasks:
- 1. The playbook installs the docker.io
- 2. Next the playbook installs pip. This manages the software packages written in Python 3.
- 3. Lastly we will download and launch a docker Elk Container. 


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

- Copy the install-elk.yml to /etc/ansible.
- Update the install-elk.yml file to include the install docker.io, Install pip3 features, and the Install Docker python module. 
- Run the playbook, and navigate to http//(elk public ip here)5601:/app/Kibana to check that the installation worked as expected.
- 

### Commands to Install Filebeat on the DVWA Container
 1- Run docker start elk
 2- Run docker container list -a
 3- Open a terminal and SSH into your jump box:
    - Start the Ansible container.
    - SSH into the Ansible container.
    -Run: curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat >> /etc/ansible/filebeat-config.yml
4- Scroll to line #1106 and replace the IP address with the IP address of your ELK machine.
   - output.elasticsearch:
   - hosts: ["10.1.0.4:9200"]
   - username: "elastic"
   - password: "changeme"
5- Scroll to line #1806 and replace the IP address with the IP address of your ELK machine.
   - setup.kibana:
   - host: "10.1.0.4:560

 ### Creating the Filebeat Installation Play
    - Download the .deb file from artificats.elastic.co
    - Run: dpkg -i filebeat-7.4.0-amd64.deb
    - After entering your information into the Filebeat configuration file and Ansible playbook, 
    - Run: ansible-playbook filebeat-playbook.yml
    - Then varify the playbook is complete
