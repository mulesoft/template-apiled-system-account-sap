
# Anypoint Template: API Led Connectivity System API for SAP

+ [License Agreement](#licenseagreement)
+ [Use Case](#usecase)
+ [Considerations](#considerations)
	* [SAP Considerations](#sapconsiderations)
+ [Run it!](#runit)
	* [Running on premise](#runonopremise)
	* [Running on Studio](#runonstudio)
	* [Running on Mule ESB stand alone](#runonmuleesbstandalone)
	* [Running on CloudHub](#runoncloudhub)
	* [Deploying your Anypoint Template on CloudHub](#deployingyouranypointtemplateoncloudhub)
	* [Properties to be configured (With examples)](#propertiestobeconfigured)
+ [API Calls](#apicalls)
+ [Customize It!](#customizeit)
	* [system-api-sap.xml](#systemapisap)



# License Agreement <a name="licenseagreement"/>
Note that using this template is subject to the conditions of this [License Agreement](AnypointTemplateLicense.pdf).
Please review the terms of the license before downloading and using this template. In short, you are allowed to use the template for free with Mule ESB Enterprise Edition, CloudHub, or as a trial in Anypoint Studio.

# Use Case <a name="usecase"/>
This Anypoint Template should serve as a foundation for API Led Connectivity approach of running an enterprise.
The template is a System API to underlying SAP system.

This Anypoint Template is a REST API implemented using APIkit and RAML definition. The basic CRUD operations are implemented for Account object (Customer). The API uses JSON as an exchange format. Included are example requests and responses.

Below are the endpoints that are implemented.

### GET /accounts
Retrieves accounts from SAP system based on the combination of query parameters. At least one of `modifiedAfter` or `name` should be set to retrieve results. Look at the included RAML definition to learn more about the implemented query parameters.

### POST /accounts
Inserts new Account to SAP system (Customer)

### GET /accounts/{id}
Retrieves an Account (Customer) based on the given SAP native identifier.

### PUT /accounts/{id}
Updates an Account (Customer) with the data in the HTTP request. All fields are overwritten.

### DELETE /accounts/{id}
Deletes specific Account (Customer) based on the given SAP native identifier.


Look at the included self-descriptive RAML definition and the corresponding flows to learn more about the flows.

# Considerations <a name="considerations"/>

To make this Anypoint Template run, there are certain preconditions that must be considered. All of them deal with the preparations, that must be made in order for all to run smoothly.
**Failing to do so could lead to unexpected behavior of the template.**

Before continue with the use of this Anypoint Template, you may want to check out this [Documentation Page](http://www.mulesoft.org/documentation/display/current/SAP+Connector#SAPConnector-EnablingYourStudioProjectforSAP), that will teach you how to work with SAP and Anypoint Studio.

## Disclaimer

This Anypoint template uses a few private Maven dependencies from Mulesoft in order to work. If you intend to run this template with Maven support, you need to add three extra dependencies for SAP to the pom.xml file.


## SAP Considerations <a name="sapconsiderations"/>

There may be a few things that you need to know regarding SAP, in order for this template to work.


### As destination of data

There are no particular considerations for this Anypoint Template regarding Sap as data destination.



# Run it! <a name="runit"/>
Simple steps to get API Led Connectivity System API for SAP running.


## Running on premise <a name="runonopremise"/>
In this section we detail the way you should run your Anypoint Template on your computer.


### Where to Download Mule Studio and Mule ESB
First thing to know if you are a newcomer to Mule is where to get the tools.

+ You can download Mule Studio from this [Location](http://www.mulesoft.com/platform/mule-studio)
+ You can download Mule ESB from this [Location](http://www.mulesoft.com/platform/soa/mule-esb-open-source-esb)


### Importing an Anypoint Template into Studio
Mule Studio offers several ways to import a project into the workspace, for instance:

+ Anypoint Studio Project from File System
+ Packaged mule application (.jar)

You can find a detailed description on how to do so in this [Documentation Page](http://www.mulesoft.org/documentation/display/current/Importing+and+Exporting+in+Studio).


### Running on Studio <a name="runonstudio"/>
Once you have imported you Anypoint Template into Anypoint Studio you need to follow these steps to run it:

+ Locate the properties file `mule.dev.properties`, in src/main/resources
+ Complete all the properties required as per the examples in the section [Properties to be configured](#propertiestobeconfigured)
+ Once that is done, right click on you Anypoint Template project folder
+ Hover you mouse over `"Run as"`
+ Click on `"Mule Application"`
In order to make this Anypoint Template run on Mule Studio there are a few extra steps that needs to be made.
Please check this Documentation Page:

+ [Enabling Your Studio Project for SAP](http://www.mulesoft.org/documentation/display/current/SAP+Connector#SAPConnector-EnablingYourStudioProjectforSAP)

### Running on Mule ESB stand alone <a name="runonmuleesbstandalone"/>
Complete all properties in one of the property files, for example in [mule.prod.properties](../master/src/main/resources/mule.prod.properties) and run your app with the corresponding environment variable to use it. To follow the example, this will be `mule.env=prod`.


## Running on CloudHub <a name="runoncloudhub"/>
While [creating your application on CloudHub](http://www.mulesoft.org/documentation/display/current/Hello+World+on+CloudHub) (Or you can do it later as a next step), you need to go to Deployment > Advanced to set all environment variables detailed in **Properties to be configured** as well as the **mule.env**.


### Deploying your Anypoint Template on CloudHub <a name="deployingyouranypointtemplateoncloudhub"/>
Mule Studio provides you with really easy way to deploy your Template directly to CloudHub, for the specific steps to do so please check this [link](http://www.mulesoft.org/documentation/display/current/Deploying+Mule+Applications#DeployingMuleApplications-DeploytoCloudHub)


## Properties to be configured (With examples) <a name="propertiestobeconfigured"/>
In order to use this Mule Anypoint Template you need to configure properties (Credentials, configurations, etc.) either in properties file or in CloudHub as Environment Variables. Detail list with examples:

### Application configuration
**Common configuration**

+ http.port `9090`

**SAP Connector configuration**

+ sap.jco.ashost `your.sap.address.com`
+ sap.jco.user `SAP_USER`
+ sap.jco.passwd `SAP_PASS`
+ sap.jco.sysnr `14`
+ sap.jco.client `800`
+ sap.jco.lang `EN`
+ sap.default.accountGroup `ZAG1`

**API configuration**

+ api.domain `your-sap-api.cloudhub.io`
+ api.basePath `/api`


# Customize It!<a name="customizeit"/>
This brief guide intends to give a high level idea of how this Anypoint Template is built and how you can change it according to your needs.
As mule applications are based on XML files, this page will be organized by describing all the XML that conform the Anypoint Template.
Of course more files will be found such as Test Classes and [Mule Application Files](http://www.mulesoft.org/documentation/display/current/Application+Format), but to keep it simple we will focus on the XMLs.

Here is a list of the main XML files you'll find in this application:

* [template-apiled-system-account-sap.xml](#systemapisap)

## template-apiled-system-account-sap.xml<a name="systemapisap"/>

A functional aspect of this Anypoint Template implemented in this XML is to create or update objects in the destination system for a represented use case. You can customize and extend the logic of this Anypoint Template in this XML to more specifically meet your needs.

Configuration for Connectors and [Properties Place Holders](http://www.mulesoft.org/documentation/display/current/Configuring+Properties) are also set in this file. **Even though you can change the configuration here, all parameters that can be modified here are in properties file, and this is the recommended place to do it so.** Of course if you want to do core changes to the logic you will probably need to modify this file.

In the visual editor they can be found on the *Global Element* tab.
