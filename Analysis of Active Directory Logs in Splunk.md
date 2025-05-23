# Analysis of Active Directory Logs using Splunk
Active Directory (AD) is used to store databases and directories of users, applications, and groups, which connect the users to particular information that they need for work in the organization. AD also provides centralized authentication and authorization. Analysing these AD logs using Splunk SIEM gives insight into Windows security and operational events 

## Steps:
### Step 1: Installing and configuring
- Install Splunk Enterprise on the monitoring system.
- Windows server with Active Directory Domain Services(AD DS) on your system.
- Install Universal Forwarder on the AD DS Server to forward logs to Splunk
### Step 2: Configuration of Data inputs
- In Splunk, go to settings-> Data inputs.
- Add new->forwarded data 
- Configure the data to receive forwarded logs from the Universal Forwarder installed on the AD DS server.

Here we are using already configured and indexed logs for our analysis.
### Step 3: Analyzing Security Events from AD
- Go to Splunk Search and enter the below query to analyse the failed login attempts and account lockouts.

  *index=<index_name> sourcetype=<sourcetype_name> EventCode=4625* (failed login)
  
  *index=<index_name> sourcetype=<sourcetype_name> EventCode=4740* (account lockout)
