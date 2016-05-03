# Azure AD Connect Configuration Documenter

AAD Connect configuration documenter is a tool to generate documentation of an Azure AD Connect Connect installation. Currently, the documentation is only limited to the Azure AD Connect sync configuration.

The goal of this project is to:

* To enable quick understanding of the synchronisation configuration and "how it happens"!
* To build confidence in getting things right when making changes to the default configuration!!
* To know what was changed when you applied a new build of Azure AD Connect!!!

Prerequisites:

1. .NET Framework 4.5 to be able to run the tool
2. A fair understanding of MIIS 2003 / ILM 2007 / FIM 2010 / MIM 2016 sync engine technical concepts to be able to understand the report.

How to use the tool:

* Download the latest release from the [releases](https://github.com/Microsoft/MIMWAL/releases) tab under the Code tab tab and extract the zip file to an empty local folder on a machine which has .NET Framework 4.5 installed.
	* This will extract the Documenter application binaries along with the sample data files for "Contoso".
	* Make sure that the tool runs by double-clicking on the cmd file AzureADConnectSyncDocumenter.cmd.
* Export the Server Configuration of your pilot / test Azure AD Connect sync server by running Get-ADSyncServerConfiguration cmdlet defined in ADSync module shipped with Azure AD Connect.

```PowerShell

	Import-Module ADSync 
	Get-ADSyncServerConfiguration -Path "<CompletePathToOutputFolder>"

```

* Copy the configuration export files produced in the previous step to a folder under the "Data" directory of the Documenter tool.
	* e.g. the "Pilot" configuration files for the customer "Contoso" are provided as a sample under the "Data\Contoso\Pilot" folder.
* If you want to document the changes from a specific baseline, export the server configuration of your baseline / production Azure AD Connect server and copy the output to a folder under the Documenter "Data" directory.
	* e.g. the "Production" configuration files for the customer "Contoso" are provided as a sample under the "Data\Contoso\Production" folder.
* Edit AzureADConnectSyncDocumenter.cmd for the values of "Pilot" and "Production" directories.
	* If you don't have a baseline / production config, specify the same path as the "Pilot" config.
* Run the updated batch file. Upon successful execution, the generated report will be found in the Documenter "Report" folder. 


