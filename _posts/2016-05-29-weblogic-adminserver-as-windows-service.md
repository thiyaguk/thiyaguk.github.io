---
layout: post
title: Weblogic AdminServer as Windows service
---
To start the WebLogic AdminServer to start automatically when you boot / reboot a Windows host, you need to add it as a Windows service.

To add Weblogic as windows service,

1. create a batch file using the below commands. Change the values according to your environment. 

        SETLOCAL
        set DOMAIN_NAME=cluster_domain
        set USERDOMAIN_HOME=D:\Oracle\Middleware\user_projects\domains\cluster_domain 
        set SERVER_NAME=AdminServer
        set WL_HOME=D:\Oracle\Middleware\wlserver_10.3
        set WLS_USER=WeblogicAdm
        set WLS_PW=PaSSword
        set PRODUCTION_MODE=true
        set MEM_ARGS=-Xms512m –Xmx512m
        call D:\Oracle\Middleware\wlserver_10.3\server\bin\installSvc.cmd
        ENDLOCAL

2. Run the batch file as a administrator user account.
3. After running the script successfully, you can find the service as “beasvc cluster_domain_AdminServer” in service.msc utility
