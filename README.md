# Loading Red Hat Middleware into into OpenShift

Greetings and welcome to the Middleware you can use during the OpenShift Travel Hackathon. Using any of the software 
located here is sufficient to meeting the application requirements. 

## Assumptions
1. You have already logged into your OpenShift professional account with the _oc_ command line. 
2. You already have a project in OpenShift. In this document we will call your project _MY-PROJECT_

## Steps to getting going

You need to do these steps no matter which Middleware you are going to use.
Do all the following from the command line:

1. `oc create -f https://https://raw.githubusercontent.com/redhat-middleware-hackathon/openshift-files/master/jboss-image-streams.json  `
2. `oc policy add-role-to-user view system:serviceaccount:MY-PROJECT:default`

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

STILL NEEDED - list of software and what it does