# Loading Red Hat Middleware into into OpenShift

Greetings and welcome to the Middleware you can use during the OpenShift Travel Hackathon. Using any of the software 
located here is sufficient to meeting the application requirements. 

You are currently looking at the README.md for a 
[github repository](https://github.com/redhat-middleware-hackathon/openshift-files). The directories listed below 
refer to the directories in this repository. 

## Assumptions
1. You have already logged into your OpenShift professional account with the _oc_ command line. 
2. You already have a project in OpenShift. In this document we will call your project _MY-PROJECT_

## Steps to getting going

You need to do these steps no matter which Middleware you are going to use. Be sure to change the [My-Project] in the second command to your project name. 
Do all the following from the command line:

1. `oc create -f https://raw.githubusercontent.com/redhat-middleware-hackathon/openshift-files/master/jboss-image-streams.json  `
2. `oc policy add-role-to-user view system:serviceaccount:[MY-PROJECT]:default`

## Choosing your Software

Use the table below to chose which software you want. Once you have chosen the software you want, go into the folders
in this repository that matches the software. The files in these directories will load a template (a specification file) 
that knows how to load everything up ready for your use. For example, https://github.com/redhat-middleware-hackathon/openshift-files/blob/master/tomcat/jws31-tomcat8-postgresql-s2i.json,
this file will load up PostgreSQL and Tomcat8 together, all wired up and ready to go. 

Once you have chosen the software you want, you have two choices:
1. Clone this repo to your local machine, find the location of the file you want, and then do the following command:
`oc create -f <path to your file>/file_name.json`

2. In GitHub, click on the file link, then on the next page click on the "raw" button on the right side above the file. 
Once you are looking at the raw file, copy the URL from your browser. Now do the following command:
`oc create -f <url you just copied>` 

Once that is done - you have two methods to use the templates you just added to your project:

1. In the web console, go to the Add Project button and then in the catalog, under Java, you should see a new template for the one you added. This may be under the product name you added. For example, EAP-basic will end up under the EAP category.
2. Using the command line you can do:
    a. oc get templates (this will give you a list of the templates in your project)
    b. oc describe templates [your template of interest] (this will show you the possible parameters you can fill in
    c. oc new-app [your template of interest] -p parameter1=value1 paratermeter2=value2

## Software and short blurb

| Product | Project | Description |
| ------- | ------- | ------- |
|JBoss EAP|Wildfly|Optimized for cloud and container environments, Red Hat JBoss Enterprise Application Platform is a market-leading, Java EE-certified platform built to meet the demands of today's web-scale applications.|
|Tomcat (JWS)|Tomcat|Red Hat's supported Tomcat|
|AMQ|Artemis|JBoss A-MQ is a lightweight, high-performance messaging platform. Its modular architecture and  support for multiple standards enables real-time integration to all facets of an enterprise.|
|processserver (BPM Suite)|jBPM + Drools + Optaplanner|JBoss BPM Suite is an open source business process management platform.  It enables users to capture business processes, automate business operations and accelerate application development|
|decisionserver (BRMS)|Drools + Optaplanner|JBoss BRMS is an open source Business Rules Management System. It enables users to capture business logic, automate business decisions and accelerate application development.|
|OpenJDK|The OpenJDK|Used for building any Java project that uses just the JDK, like Vert.x or Wildfly.Swarm|
|datagrid (JDG)|Infinispan|JDG is an enterprise open source in-memory data management store, used as Distributed cache, NoSQL database and Event broker.|
|datavirt (JDV)|Teiid|Offers a relational abstraction of all information sources that is highly performant and allows for integration with your existing relational tools. Teiid has an accompanying easy-to-use design tool that enables data architects to integrate disparate information in minutes.|
|sso (RHSSO)|Keycloack|An Identity and Access Management solution aimed at modern applications and services. It makes it easy to secure applications and services with little to no code.  |



