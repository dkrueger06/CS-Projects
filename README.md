# CS-Projects
Course Projects
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![RedTeam Network Diagram](https://github.com/dkrueger06/CS-Projects/blob/main/images/RedTeam%20Network%20Diagram.jpg)

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
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.6             |
| ElkBot1  | No                  | 10.2.0.4             | 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible playbooks can be used to push commands onto a group VMs simultaneously. Which saves valuable time, money, and brain cells.

The playbook implements the following tasks:
- _Installs Docker_
- _Installs Docker's Python module_
- _Launches a Docker ELK container_

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![sudo docker ps](https://github.com/dkrueger06/CS-Projects/blob/main/images/sudo%20docker%20ps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web-1 10.0.0.5_
- _Web-2 10.0.0.6_

We have installed the following Beats on these machines:
- _Filebeat on ElkBot1_
- _Metricbeat on Web-1 and Web-2_

These Beats allow us to collect the following information from each machine:
- _Filebeat collects log data such as syslog files which record system messages on a designated server._ 
- _Metricbeat collects system data such as CPU or memory usage._

Here is an example of what you may find with Metricbeat:

![Metricbeat](https://github.com/dkrueger06/CS-Projects/blob/main/images/Metricbeat.PNG)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Simply copy the **_install_elk_** file to **_ensure success._**
- Update the **_hosts.yml_** file to include _the newly configured ELK machine._
- Run the playbook, and navigate to **_your new ELK machine or the website listed below_** to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
1. Which file is the playbook? Where do you copy it?
   - _Files found in the /ansible/roles directory are the playbooks that will set up the Beats. Copy them into the /etc/ansible/ directory._
2. Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
   - _Update the hosts.yml file to specify which machine to run your playbooks on._
3. Which URL do you navigate to in order to check that the ELK server is running?
   - _http://40.114.114.133:5601/app/kibana_

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
**Navigate to the location of your playbook and run ansible-playbook [insert name of playbook here]
 - Example: 
 - cd~ 
 - cd /etc/ansible/roles 
 - ansible-playbook filebeat-playbook.yml

The output should look something like this:

![Output](https://github.com/dkrueger06/CS-Projects/blob/main/images/Output.PNG)

