## White-list for all pools accept by the community.  


| 1 | IP | Owner | Purpose | Frontend/stats | Pool CFG |
|:-:|:-|:-:|:-:|:-| :-|
|2|37.187.27.30:13655 |Edward|Explorer|http://xdagscan.com/|
|3|195.201.168.17:16775|Kbs1|Explorer|https://explorer.xdag.io/|
|4|136.243.57.79:13655|Edward|Pool|http://136.243.57.79/stats.txt|
|5|136.243.55.153:16775|Kbs1|Explorer|http://explorer.xdag.io|
|6|
|7|
|8|
|9|
|10|
|11|
|12|
|13|
|14|
|15|
|16|
|17|
|18|
|19|
|20|
|21|
|22|
|23|
|24|
|25|
|26|
|27|
|28|
|29|
|30|
|31|
|32|
|33|
|34|
|35|
|36|
|37|
|38|
|39|
|40|




***

### POOL OWNERS' AGREEMENT

Due to the recent events the following recommendations and decisions have been made by the community and developer team.  

Only use pools listed in the whitelist. Even though it’s very restraining in its current state, using only approved pools is vital for the health of the network. For now, every submission regarding whitelist addition will be audited, and only one pool will be added to whitelist per week. This will continue until the network is fully stable. The following requirements have to be fulfilled in order to apply for a pool:  

1. **No private pools**  
1. **A public frontend would be appreciated. If you don’t want to add one, please provide at least:**  
   1. **Pool `state` must be exposed in real time (maximum interval time: one minute) by HTTP.**  
   1. **Pool `stats` must be exposed in real time (maximum interval time: one minute) by HTTP.**  
   1. **Pool `net conn` must be exposed in real time (maximum interval time: one minute) by HTTP.**  
1. **Server time zone must be set to UTC time zone.**  
1. **Must use ntpdate to synchronize time.**  
1. **Must use root or unlimited user (max open files limit set to more then 4096) to start pool process.**  
1. **Do not try to change the hardcode of max miners.**  
1. **Server configuration with 8-core CPU, 32G RAM, SSD raid0/raid10 and above.**  
1. **1Gbit/s Internet Speed and above.**  
1. **Do not block other pools to synchronize.**  
1. **The contact person of a pool must be added to the Discord poolowner group.**  

Regarding whitelist additions, please send your requests to: pool@xdag.io. No other ways will be accepted for now.

In your email request, please include this list and fill out everything.

1. Pool node IP and port:  
1. Pool configuration:  
   1. Pool config:  
   1. NTP config:  
   1. Timezone config:  
3. Pool hardware configuration:  
   1. CPU:  
   1. RAM:  
   1. Disk:  
   1. Internet bandwidth:  
4. Pool frontend:  
   1. `state` through HTTP:  
   1. `stats` through HTTP:  
   1. `net conn` through HTTP:  
   1. Pool frontend link (optional):  
5. Pool owner: (Discord username is better for communication.)  

You will receive an invitation to join Discord from pool@xdag.io.  

***

**Example of a properly filled out request** (XDAG v0.2.3):

1. Pool node IP and port: 52.69.99.30:13655
2. Pool configuration:
   1. Pool config: 52.69.99.30:13654:8192:1024:1024:1:10:5:1
   1. NTP config: sudo ntpd -s pool.ntp.org
   1. Timezone config:  
   $timedatectl  
   Local time: Tue 2018-06-05 18:00:05 UTC  
   Universal time: Tue 2018-06-05 18:00:05 UTC  
   RTC time: Sun 2018-05-27 14:02:59  
   Time zone: Etc/UTC (UTC, +0000)  
   Network time on: yes  
   NTP synchronized: yes  
   RTC in local TZ: no  
3. Pool hardware configuration:  
   1. CPU: Intel(R) Xeon(R) Platinum 8175M CPU @ 2.50GHz 16 Cores
   1. RAM: 64GB 
   1. Disk: 100GB + 300GB + 100GB SSD
   1. Internet bandwidth: 10Gbps
4. Pool frontend:  
   1. state through HTTP: http://pool.xdag.us/state.txt
   1. stats through HTTP: http://pool.xdag.us/stats.txt
   1. net conn through HTTP: http://pool.xdag.us/netconn.txt
   1. Pool frontend link (optional): http://pool.xdag.us/index.html
5. Pool owner: Frozen (Discord: frozen#0085)

***

### Tips:  
* Please use UTC time and sync time on pool server with the nearest source from http://www.pool.ntp.org/  
`ntpupdate -s servername`  

* Please use `cat /proc/cpuinfo` to get CPU info.  

* Please use `cat /proc/meminfo` to get RAM info.  

* Please modify `/etc/security/limits.conf` to set open file limit.  
  Example:  
`* soft nofile 65536`  
`* hard nofile 65536`  

* Please use `ulimit -a` to get max open file info.  

* Please use `timedatectl` get to timezone info.  

* `state` is xdag command, export this information at least once per minute.  
`echo -e "state\nexit\n" | ./xdag -i > state.txt`  

* `stats` is xdag command, export this information at least once per minute.  
`echo -e "stats\nexit\n" | ./xdag -i > stats.txt`  

* `net conn` is xdag command, export this information at least once per minute.  
`echo -e "net conn\nexit\n" | ./xdag -i > netconn.txt`  

* The public HTTP access links should be like below and updated at least once per minute:   
http://pool.xdag.us/state.txt  
http://pool.xdag.us/stats.txt  
http://pool.xdag.us/netconn.txt  

* Please set your firewall or iptable correctly for other pools to connect.  

---
Maintainer:  [Frozen](https://github.com/xrdavies)