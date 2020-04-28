# VPNAccountOpening
Automate VPN account opening process by using IBM BPM - BAW &amp; RPA

## Summary

This asset is created to show how to define a workflow nside [IBM BAW](https://www.ibm.com/products/business-automation-workflow) (Business Automation Workflow) including UI designs and [IBM RPA](https://www.ibm.com/automation/rpa) integration. 

It can be used by any organization using VPN solutions and easily adapted to their VPN systems. In this scenario, we are using a basic desktop application to simulate a legacy system which doesn't accept integration. 

## Shared Know-How
 * IBM BAW:
    * Implementing a workflow
    * Implementing user interfaces 
    * How to start RPA tasks inside a process
    * Sending E-mail
  * IBM RPA:
    * Implementing a robot task
    * Gathering data from BAW
    * Call 3rd party scripts from robot task
    * Sending E-mail


## Product Versions
| Product       | Version       | 
| ------------- |:-------------:| 
| BAW       | 19.0.0.3		|	 
| RPA    |  11.0.0.7    |

##  PreRequirements
* DB2 Database
* Common Toolkit should be imported to your BAW. Check the [repository](https://github.com/DBA-Turkiye/BAWCommonToolkit) and documentation for more information. 

You can find the summary of required actions in order to import BAW & RPA project below. 
## BAW - Business Automation Workflow
### Execute DB Scripts
Execute scripts inside [SQL Scripts](https://github.com/DBA-Turkiye/VPNAccountOpening/tree/master/SQLScripts) folder. Be sure that you have followed the required steps to import Common Toolkit [repository](https://github.com/DBA-Turkiye/BAWCommonToolkit) and executed DB Scripts inside there.

These scripts includes required parameters to be use inside this project such Sypmtoms for COVID-19, Gender, Medical Disease types, City, County information and some approval status parameters. 

###  6.2. <a name='ImportProcessApplication'></a> Import Process Application

For more details you can check: [Importing and Exporting Process Applications](https://www.ibm.com/support/knowledgecenter/SS8JB4/com.ibm.wbpm.admin.doc/topics/managing_process_applications_E.html)

* Open IBM Workflow Center - https://YOURIP:PORT/WorkflowCenter/
* Click Import Process App
* Click Choose File to select Process Application file with .twx extension. You can download the latest version of the Process App from [BAW folder](https://github.com/DBA-Turkiye/VPNAccountOpening/tree/master/BAW) under this repo.  
* In the Import Process App window, a name and acronym have been specified based on information in the file you selected.
* You can filter the messages by clicking Errors or Warnings.

###  Add Environment Variable

* Open Process App Settings
* Click Environment Variables
* Add a new Environment Variable with below parameters if not exists
  * Key: DataSourceName
  * Default: jdbc/IBMCloudDB2 - Be sure that you have defined Data source inside WAS as defined in the toolkit repository [documentation](https://github.com/DBA-Turkiye/BAWCommonToolkit#define-jdbc-resource-on-was).


