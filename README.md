# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

1. Update the path with the name of your diagram](Images/diagram_filename.png)

   https://drive.google.com/file/d/1_g3QUVIZgUr-s7_x2Olq24MPz27PtD6F/view?usp=sharing


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

2.  Enter the playbook file.		

    install-elk.yml
  

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.

1.  What aspect of security do load balancers protect? 

    Load balancing adds additonal layers of security and protects against a distributed denial-of-service (DDoS) attack.

2.  What is the advantage of a jump box?

    The advantage of a jump box is a secure computer which acts as a single point for traffic from its origination to connect to other servers or environments.

    Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

3.  What does Filebeat watch for?

    Filebeat monitors logs files.

4.  What does Metricbeat record?

    Metricbeat monitors metrics from the operating system and services running on the server.

The configuration details of each machine may be found below.
Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky"> 			Name 		</th>
    <th class="tg-0pky"> 			Function 		</th>
    <th class="tg-0pky"> 			IP 			Address 		</th>
    <th class="tg-0pky"> 			Operating 			System 		</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c3ow"> 			Jump 			Box 		</td>
    <td class="tg-0pky"> 			Gateway 		</td>
    <td class="tg-0pky"> 			10.1.0.5 		</td>
    <td class="tg-0pky"> 			Linux 		</td>
  </tr>
  <tr>
    <td class="tg-0pky"> 			Web 			1 		</td>
    <td class="tg-0pky"> 			VM 		</td>
    <td class="tg-0pky"> 			10.1.0.6 		</td>
    <td class="tg-0pky"> 			Linux 		</td>
  </tr>
  <tr>
    <td class="tg-0pky"> 			Web 			2 		</td>
    <td class="tg-0pky"> 			VM 		</td>
    <td class="tg-0pky"> 			10.1.0.7 		</td>
    <td class="tg-0pky"> 			Linux 		</td>
  </tr>
  <tr>
    <td class="tg-0pky"> 			ELK 		</td>
    <td class="tg-0pky"> 			VM 			(Monitor) 		</td>
    <td class="tg-0pky"> 			10.2.0.4 		</td>
    <td class="tg-0pky"> 			Linux 		</td>
  </tr>
  <tr>
    <td class="tg-0pky"> 			DVWA 			3 		</td>
    <td class="tg-0pky"> 			VM 		</td>
    <td class="tg-0pky"> 			10.4.0.4 		</td>
    <td class="tg-0pky"> 			Linux 		</td>
  </tr>
  <tr>
    <td class="tg-0pky"> 			DVWA 			4 		</td>
    <td class="tg-0pky"> 			VM 		</td>
    <td class="tg-0pky"> 			10.4.0.5 		</td>
    <td class="tg-0pky"> 			Linux 		</td>
  </tr>
</tbody>
</table>

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

1.  Add whitelisted IP addresses	68.100.69.36

    Machines within the network can only be accessed by jump box.

2.  Which machine did you allow to access your ELK VM? 
 
    Jump box

3.  What was its IP address? 

    10.1.0.5

A summary of the access policies in place can be found in the table below.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-baqh{text-align:center;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-baqh">Name</th>
    <th class="tg-baqh">Publicly Accessed</th>
    <th class="tg-baqh">Allowable IP Addresses</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">Jump Box</td>
    <td class="tg-0lax">No</td>
    <td class="tg-0lax">10.1.0.5</td>
  </tr>
  <tr>
    <td class="tg-0lax">Web1 &amp; 2</td>
    <td class="tg-0lax">No</td>
    <td class="tg-0lax">10.1.0.6 and 10.1.07</td>
  </tr>
  <tr>
    <td class="tg-0lax">DVWA 1&amp; 2</td>
    <td class="tg-0lax">No</td>
    <td class="tg-0lax">10.4.0.4 and 10.4.0.5</td>
  </tr>
</tbody>
</table>

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

1.What is the main advantage of automating configuration with Ansible?

  The main advantage of automating configuration with ansible is it’s agentless, meaning less maintenance overhead , performance degradations and compatible with     legacy device. In addition, it’s idempotency which it can apply an operation once or many times with the same result.  YAML Playbooks are a  better fit than       other formats like JSON.

The playbook implements the following tasks:

2.  In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.

    Installs the docker apt module
    Installs pip3 apt module
    Installs docker python module
    Use sysctl module for more memory
    Download and launch docker container

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
1.  List the IP addresses of the machines you are monitoring.
    
    Web 1 10.1.0.6
    Web 2 10.1.0.7

We have installed the following Beats on these machines:
2. Specify which Beats you successfully installed

   Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

3. In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which    we use to track user logon events, etc.

  Filebeat generates log files and forwards them to Elastaticsearch, Logstash and Kibana (ELK) for indexing while Metricbeats collects metrics from the operating
  system and from services running on the server

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to /etc/ansible directory.
- Update the /etc/ansible/hosts file to include private IP addresses for the VMs
- Run the playbook, and navigate to curl localhost/setup.php to check that the installation worked as expected.

Answer the following questions to fill in the blanks:

1. Which file is the playbook?  
  
   There playbooks are install-elk.yml, filebeat-playbook.yml, metricbeat-playbook.yml and ansible_config.yml

2. Where do you copy it?  

   The playbooks are located in /etc/ansible
  
3. Which file do you update to make Ansible run the playbook on a specific machine?

   The /etc/ansible/hosts is updated with hosts name and ip addresses to run the playbook on a specific machine.


4.  How do I specify which machine to install the ELK server on versus which to install Filebeat on?

    Filebeat is only installed on the client servers that need to monitored and logged.


5.  Which URL do you navigate to in order to check that the ELK server is running?  

    http : // VM’s IP:5601/app/kibana

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc. 
    
    install-elk.yml, install-filebeat.yml, install-metricbeat.yml
