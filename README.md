# Send Emails plugin
This document describes how to set up 
- SendEmailsToMemebersSecurityRole
- SendEmailsToChildIncidentCreator

## Instructions
1. Create entity [`emailnotify`]
2. Add attributes
	
    -[`subject`] 		(single line text)
	
    -[`body`] 			(single line text)
	
    -[`incident_lookup`]	(lookup; add lookup target to incident)
3. Add attribute to Incident [incident] entity

    -[`primary_incident`]	(lookup; add lookup target to incident)
4. Add plugins to your organization 

    -download .zip files from this repository (`SendEmailsToMemebersSecurityRole.zip`; `SendEmailsToChildIncidentCreator`)
    
    -add -zip files to your organization
5. Add bellow commands to your process (Incident changed)
    
    Plugin.SendEmailsToChildIncidentCreator([`incidentid`], [`subject`] , [`body`] )
    
    -[`incidentid`] -primaryincidentid

    Plugin.SendSendEmailsToMemebersSecurityRole([`nameOfSecurityRole`] , [`subject`] , [`body`] , [`incidentid`] )
        
    -[`nameOfSecurityRole`] e.g. Schedule Manager

*Note: It is necessary to define incidentid as in the image below (create local string for both plugins)*


![Screenshot](process1.png)

6. Create new process for sending the emails

    -this process will start, when new record is created (`SendSendEmailsToMemebersSecurityRole` or `SendEmailsToChildIncidentCreator` created new record in backend)

![Screenshot](process2.png)

7. Congratulations, everything should work now.
