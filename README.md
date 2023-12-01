# splunk
Splunk project to create noname events to Splunk Common Information Model (CIM) mapping tool

In order to install the mapping app, we will need to configure the noname apliance as follows:

1. Create three new workflows with the follwing information

1.1 Configuration
   Integration Name - "Splunk-Issues"
   Splunk Domain URL - <Your Splunk Domain URL>
   Token - <Your Splunk Token>
    
   Define Source Type
   Custom 
   Custom Source Type - Noname-Issues

   Enterprise Extra Data
   HTTP Port Number  - <Your Splunk Domain Port>


1.2 Configuration
   Integration Name - "Splunk-Schema"
   Splunk Domain URL - <Your Splunk Domain URL>
   Token - <Your Splunk Token>
    
   Define Source Type
   Custom 
   Custom Source Type - Noname-Schema

   Enterprise Extra Data
   HTTP Port Number  - <Your Splunk Domain Port?


1.3. Configuration
   Integration Name - "Splunk-Audit"
   Splunk Domain URL - <Your Splunk Domain URL>
   Token - <Your Splunk Token>
    
   Define Source Type
   Custom 
   Custom Source Type - Noname-Audit

   Enterprise Extra Data
   HTTP Port Number  - <Your Splunk Domain Port>


2. Create three different workflow policies as follows:

  2.1 Choose Workflow Condition
      Source - Issues
      Select Group - root

      Choose Workflow Actions
      Name - Issues to Splunk
      Description - Send Noname issues to splunk
      Action - >Splunk / Splunk-Issues
      
      
  2.2 Choose Workflow Condition
      Source - Audit Log

      Choose Workflow Actions
      Name - Audit Log to Splunk
      Description - Send Noname audit logs to splunk
      Action - >Splunk / Splunk-Audit

   2.3 Choose Workflow Condition
      Source - Changes
      Select Group - root
      
      Choose Workflow Actions
      Name - Changes to Splunk
      Description - Send Changes splunk
      Action - >Splunk / Splunk-Schema


3. Log into splunk with the admin account and install the Noname mapping app
   
      

   

     
 
