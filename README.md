# CS-Projects
Course Projects
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[RedTeam Network Diagram](https://github.com/dkrueger06/CS-Projects/issues/2#issue-923192878)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select files in the [ansible](https://github.com/dkrueger06/CS-Projects/tree/main/ansible) folder may be used to install only certain pieces of it, such as Filebeat.




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
- _Load Balancers help to protect servers against DDoS attacks._
- _A Jump Box allows controlled access to two or more seperate security zones._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- _Filebeat monitors log files and specified locations. It collects log events and sends them to either Elasticsearch or Logstash to be indexed._
- _Metricbeat collects metrics from the operating system and services running on the server and ships them to Elasticsearch or Logstash._

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | DVWA     | 10.0.0.5   | Linux            |
| Web-2    | DVWA     | 10.0.0.6   | Linux            |
| ElkBot1  | Kibana   | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _24.1.39.119_

Machines within the network can only be accessed by SSH.
- _JumpBoxProvisioner, @24.1.39.119, has access to ElkBot1_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible playbooks can be used to push commands onto a group VMs simultaneously. Which saves valuable time, money, and brain cells.

The playbook implements the following tasks:
- _Installs Docker_
- _Installs Docker's Python module_
- _Launches a Docker ELK container_

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web-1 10.0.0.5_
- _Web-2 10.0.0.6_

We have installed the following Beats on these machines:
- _Filebeat on ElkBot1_
- _Metricbeat on Web-1 and Web-2_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _http://40.114.114.133:5601/app/kibana_

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
