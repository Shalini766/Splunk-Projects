# Analysis of SMTP logs using Splunk
SMTP is the Simple Mail Transfer Protocol, which is necessary for the transfer of email between two sources. SMTP log sources contain the email address of the sender, the recipient, timestamps, whether delivered or blocked, and other activity. Analysis of these logs helps to monitor email traffic and detect security threats.

## Steps
### Step 1: 
- Splunk is installed and configured to collect logs from SMTP log sources.
- Here we are using logs that are already collected by Splunk SIEM.
- Otherwise, we can also upload a sample SMTP log file to analyse.

  *Sample SMTP log>settings>add data>Upload as the data input>select file>select source type (SMTP)>submit*

  ### Step 2: Analysis
  - Go to Splunk search bar and enter the following command to see the SMTP events.
  
