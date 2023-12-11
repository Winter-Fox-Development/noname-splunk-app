# Splunk Noname App
Splunk project to create Noname events to Splunk Common Information Model (CIM) mapping tool.

In order to install the mapping app, we need to configure the Noname appliance as follows:

## Noname Setup 
To install the Noname > Splunk App, you will need to set up the Noname appliance to send data over with the right source type.
### Issues
* Configuration
   - Integration Name: `Splunk-Issues`
   - Splunk Domain URL: `<Your Splunk Domain URL - HTTPS ONLY>`
   - Token: `<Your Splunk Token>`
* Define Source Type
   - Custom 
   - Custom Source Type: `Noname-Issues`
* Enterprise Extra Data
   - HTTP Port Number: `<Your Splunk HEC Port>`
### Configuration
* Configuration
  - Integration Name: `Splunk-Schema`
  - Splunk Domain URL: `<Your Splunk Domain URL - HTTPS ONLY>`
  - Token: `<Your Splunk Token>`   
* Define Source Type
  - Custom 
  - Custom Source Type: `Noname-Schema`
* Enterprise Extra Data
  - HTTP Port Number: `<Your Splunk HEC Port>`
### Audit
* Configuration
  - Integration Name: `Splunk-Audit`
  - Splunk Domain URL: `<Your Splunk Domain URL - HTTPS ONLY>`
  - Token: `<Your Splunk Token>`
* Define Source Type
  - Custom 
  - Custom Source Type: `Noname-Audit`
* Enterprise Extra Data
  - HTTP Port Number: `<Your Splunk HEC Port>`
## Create three different workflow policies as follows:
### Splunk Issues
* Choose Workflow Condition
  - Source: `Issues`
  - Select Group: `root`
* Choose Workflow Actions
  - Name: `Issues to Splunk`
  - Description: `Send Noname issues to Splunk`
  - Action: `>Splunk / Splunk-Issues`
### Audit     
* Choose Workflow Condition
  - Source: `Audit Log`
* Choose Workflow Actions
  - Name: `Audit Log to Splunk`
  - Description: `Send Noname audit logs to Splunk`
  - Action: `>Splunk / Splunk-Audit`
### Schema 
* Choose Workflow Condition
  - Source: `Changes`
  - Select Group: `root`
* Choose Workflow Actions
  - Name: `Changes to Splunk`
  - Description: `Send Changes to Splunk`
  - Action: `>Splunk / Splunk-Schema`
## Install Noname App into > Splunk
Log into Splunk as an admin, go to the app page, click on the manage icon, and follow these instructions:
1. Click on `Install App from File`.
2. Download the file from this repository locally and choose the file `noname-1.0.0.spl`.
3. Click on upload, and then the app will be installed.
4. Verify that the new source mapping is working by searching for these commands:
   - `| datamodel Intrusion_Detection search` for Noname-Issues
   - `| datamodel Change search` for Noname-Audit and Noname-Schema
5. You can go to the app to see the default dashboard, which is the search for `| datamodel Intrusion_Detection search`.
