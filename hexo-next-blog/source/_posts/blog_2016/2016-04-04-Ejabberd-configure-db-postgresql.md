---
layout: post
title: "Configure Ejabberd chat server to use PostgreSQL"
date: 2016-04-04 19:58:00
categories: [ 开源技术]
tags:
  - chat server
  - tech
---

Configure Ejabberd chat server to use PostgreSQL
================================================
In order to make data persistent with in any application, we can link it to a PostgreSQL relational database.
 
1. To change the default to use a postgres database we first need to create a new postgresql database on the server  
```  
huazhang@zhoutekiMacBook-Air:~/ejabberd-15.09/bin$ psql
psql (9.4.4)
huazhang=# run ./createdb ejabberd
 ```
 
2. Create the tables using the supplied script    
```  
huazhang-# ./psql ejabberd < ~/ejabberd-15.09/lib/ejabberd-15.09/priv/sql/pg.sql
```
 
3. Add a user for the database  
```  
~/ejabberd-15.09/bin$ createuser -P -s -e admin  
Enter password for new role: root123  
Enter it again: root123  
CREATE ROLE testadmin PASSWORD 'md55ebf4663bc3108d036c91bc4bbcfd599' SUPERUSER CREATEDB CREATEROLE INHERIT LOGIN;  
```

4. Configure ODBC options in ejabberd.cfg:  
```  
Scroll down to the section headed Database setup.  
edit the following, remove the %% commenting  
##  
## PostgreSQL server:  
##  
odbc_type: pgsql  
odbc_server: "localhost"  
odbc_database: "ejabberd"  
odbc_username: "admin"  
odbc_password: "root123"  
```
 
5. Add _odbc to modules you wish to use the odbc database, and store messages into archive table  
```    
e.g. mod_offline_odbc instead of mod_offline.  
full list in ejabberd user guide   
## Modules enabled in all ejabberd virtual hosts.  
##    
modules:    
  #By default mod_mam does not store messages. If you like to store messages, simply add this mod_mam   option:  
  mod_mam:  
      default: always     
      db_type: odbc     
```

6. Under authentication comment out internal authentication:  
 ```    
##  auth_method:  internal  
Then un comment auth_method: odbc  
 ```

7. Register a new user and appear online using PSI client or similar application

8. Add a user to allowed admin access control list in ejabberd.cfg
 ```  
{acl, admin, {user, "username", "server"}}.  
 ```
 
9. Confirm registered user and status in web admin:  
http://serverIP:5280/admin/  

10. Connect to database using PgAdmin to view tables with data and confirm ejabberd is now using PostgreSQL

Reference
==========
Getting started with ejabberd  
[Initial setup and install of PostgreSQL Database]
(http://stackoverflow.com/questions/9753710/setup-ejabberd-with-postgresql)  