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

### Step 4: Action taken by host

-To see whether the email is delivered or blocked by the host, use the action command, and to count the number of actions, use the stats count command.

*index="***" sourcetype="*smtp*"| stats count by action,host*


  
