# Work with Oracle Database Shard
You can view the publish page by [click here]( https://minqiaowang.github.io/work-with-db-shard/workshops/freetier/)

After you reboot or scale the shard director host, please use the following step to restart the GSM.

```
$ ssh -i labkey opc@xxx.xxx.xxx.xxx
Last login: Fri Jan 29 05:02:35 2021 from 59.66.120.23
-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory

[opc@sdbsd0 ~]$ sudo service firewalld stop
Redirecting to /bin/systemctl stop firewalld.service

[opc@sdbsd0 ~]$ sudo su - oracle
Last login: Fri Jan 29 05:08:46 GMT 2021 on pts/0

[oracle@sdbsd0 ~]$ gdsctl start gsm -gsm sdbsd0
GSM is started successfully

[oracle@sdbsd0 ~]$ lsnrctl status sdbsd0

LSNRCTL for Linux: Version 19.0.0.0.0 - Production on 29-JAN-2021 06:23:27

Copyright (c) 1991, 2019, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(HOST=sdbsd0.subnet.vcn.oraclevcn.com)(PORT=1522)(PROTOCOL=tcp))(CONNECT_DATA=(SERVICE_NAME=GDS$CATALOG.oradbcloud)))
STATUS of the LISTENER
------------------------
Alias                     SDBSD0
Version                   TNSLSNR for Linux: Version 19.0.0.0.0 - Production
Start Date                29-JAN-2021 06:23:15
Uptime                    0 days 0 hr. 0 min. 11 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Listener Parameter File   /u01/app/oracle/product/19.3.0/gsmhome_1/network/admin/gsm.ora
Listener Log File         /u01/app/oracle/diag/gsm/sdbsd0/sdbsd0/alert/log.xml
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=sdbsd0.subnet.vcn.oraclevcn.com)(PORT=1522)))
Services Summary...
Service "GDS$CATALOG.oradbcloud" has 1 instance(s).
  Instance "sdbsc0", status READY, has 1 handler(s) for this service...
Service "GDS$COORDINATOR.oradbcloud" has 1 instance(s).
  Instance "sdbsc0", status READY, has 1 handler(s) for this service...
Service "_MONITOR" has 1 instance(s).
  Instance "SDBSD0", status READY, has 1 handler(s) for this service...
Service "_PINGER" has 1 instance(s).
  Instance "SDBSD0", status READY, has 1 handler(s) for this service...
The command completed successfully
[oracle@sdbsd0 ~]$ 
```

