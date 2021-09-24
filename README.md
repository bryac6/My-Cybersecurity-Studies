## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/bryac6/My-Cybersecurity-Studies/blob/main/Diagrams/Topology%20Diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.
 
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Jump boxes improve a company’s network security by having a secure central location that must be connected to first before launching any tasks.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.

- _TODO: What does Filebeat watch for? 

Filebeat monitors log files to collect log events. Information is then forwarded to either Logstash or Elasticsearch to be indexed.

- _TODO: What does Metricbeat record?

_Metricbeat records metrics from the server and OS.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| ELK-VM   | ELKServer| 10.1.0.4   | Linux            |
| Web1     | Webserver| 10.0.0.5   | Linux            |
| Web2     | Webserver| 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- _TODO: Add whitelisted IP addresses_

	MY Public IP

- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

Machines within the network can only be accessed by Jumpbox IP 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| JumpBoxb | No                  | My Public IP         |
| ELK-VM   | Yes (Port 5601 only)| Internet             |
| Web-VM   | No                  | Via Loadbalancer     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- _TODO: What is the main advantage of automating configuration with Ansible?

This helps to eliminate variability between configurations and limits multiple mistakes.


The playbook implements the following tasks:

Installs Docker
Installs Python-pip
Install Docker python module
Increases virtual memory
_Downloads and launches a docker ELK container with the following published ports: 5601 9200 5044


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
 Web-1 10.0.0.5, Web-2 10.0.0.6, Web-3 10.0.0.7

We have installed the following Beats on these machines


These Beats allow us to collect the following information from each machine:

Filebeat generates and organizes log files to send to Elasticsearch on the ELK Server. The logs contain information about the file system such as which files have changed and when.
Metricbeat collects metrics from systems and services to send to Elasticsearch on the ELK Server. The logs contain information such as CPU usage, memory, disk IO, and network IO statistic

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

Copy the install-elk.yml file to Ansible container folder /etc/ansible/files/.
Update the hosts file to include the Elk Server IP address of 10.1.0.4 under elkservers
Run the playbook, ansible-playbook elk-playbook.yml, and navigate to http://104.42.77.249:5601/app/kibana#/home to check that Kibana is running.


_TODO: Answer the following questions to fill in the blanks:_

:/etc/ansible/elk-playbook.yml. You copy it to the directory.

_Which file do you update to make Ansible run the playbook on a specific machine?

 You update the hosts file. How do I specify which machine to install the ELK server on versus which to install Filebeat on? 

Add the private IP under “servers”

_Which URL do you navigate to in order to check that the ELK server is running?

 http://104.42.77.249:5601/app/kibana#/home


