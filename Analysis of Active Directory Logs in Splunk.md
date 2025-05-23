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

  *index=<index_name> sourcetype=<sourcetype_name> EventCode=4624* (successful login)

  *index=<index_name> sourcetype=<sourcetype_name> EventCode=4625* (failed login)
  
  *index=<index_name> sourcetype=<sourcetype_name> EventCode=4740* (account lockout)
### Step 4: Creating Dashboard for Events
- Click on "Create new Dashboard".
- Add New Panel, select "Search" as data source.
- Use search query to filter logon events such as

   *sourcetype=<sourcetype_name> EventCode=4624* (successful login)

  -Configure visualization and save panel.

Now AD Logons Dashboard is created.
### Step 5: Setting up Alerts for Failed AD Logon
- Use the search query

  *index=<index_name> sourcetype=<sourcetype_name> EventCode=4625* (failed login)

- Click on "Save as Alert" and configure the settings.
  *Save as-> Alert->Title->Alert Type->Trigger Conditions->Trigger actions->Add to Triggered Alerts->Severityis High->Save*
### Step 6: Generating Report
- Save the search that you want to generate report such as
  
   *sourcetype=<sourcetype_name> EventCode=4624*

- Save as "Report" and configure the report settings.
- Now Reports will be generated for the saved search query regularly.

By using Splunk way we can analyse the AD Activity on Windows which helps in monitoring, detecting and visualizing the suspicious AD  activity and logs, and gain valuable insights into AD security and operational events.


