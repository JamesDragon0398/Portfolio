# Portfolio
Portfolio for James Reilly

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
https://drive.google.com/file/d/1SNwGLUOmjBg_38W6RkDxU0sW6z96Ye-2/view?usp=sharing)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly durable, in addition to restricting access to the network.
- Load Balancers defend an organization against Direct Denial of Service (or DDoS) attacks? A jumpbox gives you a reliable and secure computer that you can use as a origin point to connect to other machines

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system logs.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |52.229.23.31| Linux            |
| WEB-1    |          |  10.0.0.10 | Linux            |
| WEB-2    |          |  10.0.0.11 | Linux            |
| ELK      |          |40.76.47.104|                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _75.31.199.206

Machines within the network can only be accessed by JumpBox Vm "JB".
- _IP Address:52.229.23.31

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|   WEB-1  | No                  |   52.229.23.31       |
|   WEB-2  | No                  |   52.229.23.31       |
|   ELK    | No                  |   40.76.47.104       |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The primary benefit of Ansible is it allows IT administrators to automate away the drudgery from their daily tasks

The playbook implements the following tasks:
- ...Installs Python3
- ...Installs Docker Container
- ...Inscrease Virtual Memory 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![]https://drive.google.com/file/d/1SNwGLUOmjBg_38W6RkDxU0sW6z96Ye-2/view?usp=sharing

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.10, 10.0.0.11

We have installed the following Beats on these machines:
- _Filebeats

These Beats allow us to collect the following information from each machine:
- Filebeat is a lightweight shipper for forwarding and centralizing log data. Installed as an agent on your servers, Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the src file to etc/ansible/files.
- Update the hosts file to include the ELK Box IP address 
- Run the playbook, and navigate to http://40.76.47.104:5601/app/kibana#/home/tutorial/systemLogs to check that the installation worked as expected.

Commands:
To install docker: sudo apt install docker.io
To install a ubuntu server on your docker machine: sudo docker run -ti cyberxsecurity/ubuntu:bionic bash
To install anisble: sudo docker run -ti cyberxsecurity/ansible
To view your new ansible machine name: sudo docker container list -a
TO view running containers: sudo docker ps 
To start your ansible machine: sudo docker start {machine name}
To attach you ansible machine: sudo docker attach {machine name}
To run the playbook: ansible-playbook {playbookname.yml}
