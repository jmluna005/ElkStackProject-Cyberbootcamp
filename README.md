## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Untitled-1](https://user-images.githubusercontent.com/82488650/146113230-bbaafbb6-c125-49cd-b433-87a43100999e.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above.
Alternatively, select portions of the alpha.yml file may be used to install only certain pieces of it, such as Filebeat.

  - ansible-playbook filebeat-config.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

The configuration details of each machine may be found below.

| Name       | Function  | IP Address | Operating System |
|------------|-----------|------------|------------------|
| Jump box   | Gateway   | 10.0.0.4   | Linux            |
| Web-1      | Webserver | 10.0.0.7   | Linux            |
| Web-2      | Webserver | 10.0.0.8   | Linux            |
| ELK Server | ELKserver | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from home network IP.

Machines within the network can only be accessed by home network IP

A summary of the access policies in place can be found in the table below.

| Name       | Access | IP Address                 |
|------------|--------|----------------------------|
| Jump box   | No     | Home network IP            |
| Web-1      | No     | 10.0.0.4 & Home Network IP |
| Web-2      | No     | 10.0.0.4 & Home Network IP |
| ELK Server | No     | 10.0.0.4 & Home Network IP |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it minimizes the potenital for error and increases potential to save time. 
A Load Balancer was used to increase utility and functionality. This setup uses the filebeat-config.yml configuration file that was added to the ansible playbook. This main file saves time and effort because it can dictate which playbooks are in use; streamlining any future edits of the machines. 


The playbook implements the following tasks:
- Configure Webservers
- Install ELK Server
- Install Filebeat
- Install Metricbeat

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.4
- 10.0.2.9

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat forwards and centralizes log data. This information is forwarded to Elasticsearch/Logstash thus providing a GUI to simplify monitoring. 
- Metricbeat provides a way to provide information such as metrics from the operating system and from services running on a server. Metricbeat collects this data and sends it to Elasticsearch/Logstash (user specified)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the roles folder to /etc/ansible/roles.
- Update the hosts file to include webserver IP's and ELKServer IP
- Run the playbook, and navigate to HTTP://<ELKServer_Public_IP>:5601 to check that the installation worked as expected.

* Copy the roles folder (linked above) and files to /etc/ansible/roles
* Update the /etc/ansible/hosts file to include the webservers IP's and ELKServer IP
* Update each configuration file with ELKServer IP
    * Kibana - uncomment and replace localhost with local IP for ELK Server
    * Elasticsearch - uncomment and replace localhost with local IP for ELK Server
    
