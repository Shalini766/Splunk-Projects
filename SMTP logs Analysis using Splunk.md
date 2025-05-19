# Analysis of SMTP logs using Splunk
SMTP is the Simple Mail Transfer Protocol, which is necessary for the transfer of email between two sources. SMTP log sources contain the email address of the sender, the recipient, timestamps, whether delivered or blocked, and other activity. Analysis of these logs helps to monitor email traffic and detect security threats.

## Steps
### Step 1: 
- Splunk is installed and configured to collect logs from SMTP log sources.
- Here we are using logs that are already collected by Splunk SIEM.
- Otherwise, we can also upload a sample SMTP log file to analyse.

  *Sample SMTP log>settings>add data>Upload as the data input>select file>select source type (SMTP)>submit*
  
### Step 2: Analysis
 - Go to the Splunk search bar and enter the following command to see the SMTP events.
   
  *index=<your_smtp_index> sourcetype=<your_smtp_sourcetype>*

### Step 3: Identifying email traffic patterns

- Identify the top sender and recipients by using the following commands.

  *index=<your_smtp_index> sourcetype=<your_smtp_sourcetype>
| top limit=10 sender*


*index=<your_smtp_index> sourcetype=<your_smtp_sourcetype>
| top limit=10 recipient

### Step 4: Checking the action

- To see whether the email is delivered or blocked, use the action command, and to count the number of actions, use the stats count command.

*index="***" sourcetype="*smtp*"| stats count by action,host,sender,recipient*

### Step 5: Detecting Anomalies

- Identify the email pattern and count in the span of 1hr using the following command

*index=<your_smtp_index> sourcetype="*smtp*"|timechart span=1h count by _time*

- To find any attachments

*index=<your_smtp_index> sourcetype=<your_smtp_sourcetype>
| search attachment_type="unusual_type" OR attachment_size > 1000000*

### Step 6: Monitor user behaviour

- to monitor the email traffic by user or host

  *index<your_smtp_index> sourcetype=<your_smtp_sourcetype
  |stats count by action,host*

- to see the activity pattern in 1 day

  *index=<your_smtp_index> sourcetype=<your_smtp_sourcetype>
| timechart span=1d count by host*

Analyzing SMTP log files with Splunk SIEM enhances network security by monitoring email traffic, detecting anomalies, and correlating data for threat detection. By leveraging Splunk's capabilities, organizations can proactively identify and respond to email-based threats, ensuring the integrity and confidentiality of their communications.
  
