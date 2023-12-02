# Splunk Noname app
Splunk project to create noname events to Splunk Common Information Model (CIM) mapping tool

In order to install the mapping app, we will need to configure the noname apliance as follows:

## Noname setup 
in order to install the Naname >Splunk App, you would need to setup the Noname appliance send data over with the right source type
### Issues
* Configuration
   - Integration Name `Splunk-Issues`
   - Splunk Domain URL `<Your Splunk Domain URL>`
   - Token `<Your Splunk Token>`
* Define Source Type
   - Custom 
   - Custom Source Type - Noname-Issues
* Enterprise Extra Data
   - HTTP Port Number  - `<Your Splunk Domain Port>`
### Configuration
* Configuration
  - Integration Name `Splunk-Schema`
  - Splunk Domain URL `<Your Splunk Domain URL>`
  -  Token - `<Your Splunk Token>`   
* Define Source Type
  - Custom 
  - Custom Source Type `Noname-Schema`
* Enterprise Extra Data
  - HTTP Port Number  `Your Splunk Domain Port`
### Audit
* Configuration
  - Integration Name `Splunk-Audit`
  - Splunk Domain URL `<Your Splunk Domain URL>`
  - Token `<Your Splunk Token>`
* Define Source Type
  - Custom 
  - Custom Source Type `Noname-Audit`
* Enterprise Extra Data
  - HTTP Port Number `<Your Splunk Domain Port>`
## Create three different workflow policies as follows:
### Splunk Issues
* Choose Workflow Condition
  - Source `Issues`
  - Select Group `root`
* Choose Workflow Actions
  - Name `Issues to Splunk`
  - Description `Send Noname issues to splunk`
  - Action `>Splunk / Splunk-Issues`
### Audit     
* Choose Workflow Condition
  - Source `Audit Log`
* Choose Workflow Actions
  - Name `Audit Log to Splunk`
  - Description `Send Noname audit logs to splunk`
  - Action `>Splunk / Splunk-Audit`
### Schema 
* Choose Workflow Condition
  - Source `Changes`
  - Select Group `root`
* Choose Workflow Actions
  - Name `Changes to Splunk`
  - Description `Send Changes splunk`
  - Action `>Splunk / Splunk-Schema`
## Install Noname App into >Splunk
Log into spluk as an admin and got to the app page and click on the mange icon and follow these instructions
1. Click on the `Install App from File
2. Download the file on this repository locally and choose the file `noname-1.0.0.spl`
3. Click on upload and then the app will be installed
4. Verity that the new source mapping is working by seaching for these commands
   - `| datamodel Intrusion_Detection search` for Noname-Issues
   - `| datamodel Change search` for Noname-Audit and Noname-Schema
5. You can go to do the app to see the default dashboard which is the seach for  `| datamodel Intrusion_Detection search`
