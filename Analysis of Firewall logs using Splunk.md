# Analysis of Firewall Logs using Splunk
A firewall is important in monitoring incoming and outgoing traffic. These firewall logs give insight into the flow of traffic in the network, what information is being exchanged, open ports, and the source and destination IP addresses. All these will aid in the analysis of activity in the network and improve the network security.

## Steps:

### Step 1: 
- The Splunk instance is installed and configured.
- Firewall log data sources are configured to forward logs to Splunk.

Here we are using logs that are already collected by Splunk SIEM. Otherwise, we can also upload a sample firewall log file to analyse.

Sample firewall log>settings>add data>Upload as the data input>select file>select source type (Firewall)>submit

### Step 2:
- Go to the Splunk search bar and use the following command to see the events of the firewall.

  *index=<your_firewall_index> sourcetype=<your_firewall_sourcetype>*

### Step 3: 
- Identify the source and destination

*index=<your_firewall_index> sourcetype=<your_firewall_sourcetype>| table source destination*

### Step 4:
- Identify the incoming and outgoing traffic

*index=<your_firewall_index> sourcetype=<your_firewall_sourcetype>| stats count by bytes_in*

*index=<your_firewall_index> sourcetype=<your_firewall_sourcetype>| stats count by bytes_out*

### Step 5:
- Identify the action taken and the app risk

 *index=<your_firewall_index> sourcetype=<your_firewall_sourcetype> action=allowed AND app_risk=5* 

Analysing these firewall logs will help in detecting the unwanted traffic entering and also help prevent blocking the malicious websites in acccessing information by writing certain firewall rules, thus strengthening the security posture. 
