---
title: "Back and Restore InfluxDB "
date: "2017-04-09 01:32:50"
draft: false
categories: [开源技术]
hiddenFromHomePage: true
---
when I backup Influxdb on my Ubuntu 16.04 LTS on Lab,  it uses v0.10.0,  
```code
sudo service influxdb stop
sudo tar cvf influxdb.backup.2017.04.07.tar  /var/lib/influxdb/data /var/lib/influxdb/meta  /etc/influxdb/influxdb.conf
sudo service influxdb start
```

I try to restore the backup file into my personal System76 laptop which has InfluxDB v1.2.2.   It failed with error in /etc/influxdb/influxdb.conf
```code
sudo tar xvf influxdb.backup.2017.04.07.tar  -C /
```
So, I delete the /etc/influxdb/influxdb.conf and then try to install InfluxDB by the command, 
```code
sudo apt-get install influxdb 
```
Try to start the InfluxDB service by  $influxd
It says  "/etc/influxdb/influxdb.conf" not found.

So,  I have to download the official version [config.sample.toml](https://raw.githubusercontent.com/influxdata/influxdb/master/etc/config.sample.toml)
and copy it to /etc/influxdb/ folder, then rename it to influxdb.conf

Finally, it works.  
```code
sudo service influxdb start
```
