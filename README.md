<!-- vscode-markdown-toc -->
* 1. [Summary](#Summary)
* 2. [Shared Know-How](#SharedKnow-How)
* 3. [Product Versions](#ProductVersions)
* 4. [ PreRequirements](#PreRequirements)
* 5. [BAW - Business Automation Workflow](#BAW-BusinessAutomationWorkflow)
	* 5.1. [Execute DB Scripts](#ExecuteDBScripts)
	* 5.2. [ Import Process Application](#ImportProcessApplication)
	* 5.3. [ Add Environment Variable](#AddEnvironmentVariable)
* 6. [RPA - Robotic Process Automation](#RPA-RoboticProcessAutomation)
	* 6.1. [Import Tasks to RPA](#ImportTaskstoRPA)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->
# VPN Account Opening
Automate VPN account opening process by using IBM BPM - BAW &amp; RPA

##  1. <a name='Summary'></a>Summary

This asset is created to show how to define a workflow nside [IBM BAW](https://www.ibm.com/products/business-automation-workflow) (Business Automation Workflow) including UI designs and [IBM RPA](https://www.ibm.com/automation/rpa) integration. 

It can be used by any organization using VPN solutions and easily adapted to their VPN systems. In this scenario, we are using a basic desktop application to simulate a legacy system which doesn't accept integration. 

![](https://raw.githubusercontent.com/DBA-Turkiye/VPNAccountOpening/master/Documentation/images/VPN%20Request%20Diagram.png)

##  2. <a name='SharedKnow-How'></a>Shared Know-How
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


##  3. <a name='ProductVersions'></a>Product Versions
| Product       | Version       | 
| ------------- |:-------------:| 
| BAW       | 19.0.0.3		|	 
| RPA    |  11.0.0.7    |

##  4. <a name='PreRequirements'></a> PreRequirements
* DB2 Database
* Common Toolkit should be imported to your BAW. Check the [repository](https://github.com/DBA-Turkiye/BAWCommonToolkit) and documentation for more information. 

You can find the summary of required actions in order to import BAW & RPA project below. 
##  5. <a name='BAW-BusinessAutomationWorkflow'></a>BAW - Business Automation Workflow
###  5.1. <a name='ExecuteDBScripts'></a>Execute DB Scripts
Execute scripts inside [SQL Scripts](https://github.com/DBA-Turkiye/VPNAccountOpening/tree/master/SQLScripts) folder. Be sure that you have followed the required steps to import Common Toolkit [repository](https://github.com/DBA-Turkiye/BAWCommonToolkit) and executed DB Scripts inside there.

These scripts includes required parameters to be use inside this project such VPN Access type etc. 

###  5.2. <a name='ImportProcessApplication'></a> Import Process Application

For more details you can check: [Importing and Exporting Process Applications](https://www.ibm.com/support/knowledgecenter/SS8JB4/com.ibm.wbpm.admin.doc/topics/managing_process_applications_E.html)

* Open IBM Workflow Center - https://YOURIP:PORT/WorkflowCenter/
* Click Import Process App
* Click Choose File to select Process Application file with .twx extension. You can download the latest version of the Process App from [BAW folder](https://github.com/DBA-Turkiye/VPNAccountOpening/tree/master/BAW) under this repo.  
* In the Import Process App window, a name and acronym have been specified based on information in the file you selected.
* You can filter the messages by clicking Errors or Warnings.

###  5.3. <a name='AddEnvironmentVariable'></a> Add Environment Variable

* Open Process App Settings
* Click Environment Variables
* Add a new Environment Variable with below parameters if not exists
  * Key: DataSourceName
  * Default: jdbc/IBMCloudDB2 - Be sure that you have defined Data source inside WAS as defined in the toolkit repository [documentation](https://github.com/DBA-Turkiye/BAWCommonToolkit#define-jdbc-resource-on-was).

##  6. <a name='RPA-RoboticProcessAutomation'></a>RPA - Robotic Process Automation
###  6.1. <a name='ImportTaskstoRPA'></a>Import Tasks to RPA

* Create a new folder called under ..\Documents\Automation Anywhere Files\Automation Anywhere\My Tasks
* Copy both tasks under [repository](https://github.com/DBA-Turkiye/VPNAccountOpening/tree/master/RPA) to this folder. 
* Before creating a new VPN access request, be sure that you have started "Loop over IBM Business Automation Workflow tasks.atmx" robot task.
* In VPN Definition robot task path for VPN Server.exe application is defined as "C:\Users\Administrator\Desktop\VPN Server.exe", if you are planning to locate this file to another path, be sure that you change the path. (8th line in robot task)

