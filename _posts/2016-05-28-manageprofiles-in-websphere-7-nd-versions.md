---
layout: post
title: ManageProfiles in Websphere 7 ND versions
---

For 64-bit WebSphere Application Server 7.0, you must use the manageprofiles command to create profiles because the Profile Management Tool is not available for 64-bit systems.

To Create profiles, use the following commands from <WAS_HOME>/bin:

To create node: 

    #In Linux:
    ./manageprofiles.sh -create -profileName NodeProfile -profilePath ../profiles/NodeProfile -templatePath ../profileTemplates/managed -enableAdminSecurity true -adminUserName wasadmin -adminPassword Pass@123
    
    #In Windows:
    manageprofiles.bat -create -profileName NodeProfile -profilePath ../profiles/NodeProfile -templatePath ../profileTemplates/managed -enableAdminSecurity true -adminUserName wasadmin -adminPassword Pass@123
 
 To create deployment manager:
 
    #In Linux:
    ./manageprofiles.sh -create -profileName AdminProfile -profilePath ../profiles/AdminProfile -templatePath ../profileTemplates/dmgr -cellName Dmgr01node01 -nodeName Dmgr01node01 -enableAdminSecurity true -adminUserName wasadmin -adminPassword Pass@123

    #In Windows:
    manageprofiles.bat -create -profileName AdminProfile -profilePath ..\profiles\AdminProfile -templatePath ..\profileTemplates\dmgr -cellName Dmgr01node01 -nodeName Dmgr01node01 -enableAdminSecurity true -adminUserName wasadmin -adminPassword Pass@123

 To add the node  to deployment manager we need the SOAP port of the deployment manager. We can find this from AboutThisProfile.txt file from <WAS_HOME>/profiles/AdminProfile/logs. 
 
 Replace the SOAP port in the following command and run it:
 
    #In Linux:
    ./addNode.sh localhost <soapport> -conntype soap -profileName NodeProfile -username wasadmin -password Pass@123

    #In Windows:
    addNode.bat localhost <soapport> -conntype soap -profileName NodeProfile -username wasadmin -password Pass@123
 
  Now we have Deployment Manager and a Node which connected to the Deployment Manager.

