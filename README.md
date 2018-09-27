## Setup-Kerberos-Server-and-Client
Study guide to Kerberos server and Kerberos client

This installation setup requires three servers 
    . One is acting as kerberos KDC server 
    . The other two machines are client-1 and client-2. 
    
    • Kerberos KDC Server: 
    kdc.networkingstudio.org
    
    • Kerberos Client1: 
    krb-client1.networkingstudio.org
    
    • Kerberos Client2: 
    krb-client1.networkingstudio.org
    
### Note: 
The server and both client must be able to know their IP Addresses, and hostname of all other configured hosts, via ssh.
All systems must be properly configured and setup for network communication and both systems have the hostnames and IP addresses
In the configuration file: "/etc/hosts". This configuration settings must only be carried out on the server. 


### On server side
1, setup Hostnames for your project using this command:

    vim /etc/hosts

2, setup NTP server 
  a, install NTP server packet:
  
    yum install ntp
    
  The time and country values (e.g. for Ireland "ie")
  In most cases pool.ntp.org are used to find an NTP server.
  
  In my case I used "0.ie.pool.ntp.org, and 1.ie.pool.ntp.org"
  
    . Firstly you have to go to the offical page for "NTP public pool time servers" and chose from the list
    
    . Search for your Country location
    
    . A list of NTP servers should appear
    
### NTP server Country location code
    
![ntp server for ireland](https://user-images.githubusercontent.com/22172433/46115511-32e4cc80-c1ef-11e8-8c7c-afd4e48d3d1d.PNG)

  b, after NTP server is installed use this command: 
  
        vim /etc/ntp.conf
        
3, Using the above command you open NTP daemon main configuration file for editing 
    . Uncomment the default list,
   The NTP public servers 
    . From pool.ntp.org replace it with the list provided for your country 
    . See the screenshot above example for Ireland
    
4, You shloud allow client to have access from networks connection to synchronize time with server
    in most cases you will find the below line already present
    
    . To accomplish this, add the following line if NOT present in NTP configuration file
    . Where restrict statement controls is
            You should see what network is allowed and to query
    The synchronized time 
        . Replace network IP Address and subnetmasks accordingly as this example: 
        Note: make no changes to this below example 
        
        "restrict 192.168.1.0 netmask 255.255.255.0 nomodify notrap"
        
5, For an additional information to NTP server troubleshooting, just in case there are problems while configuring NTP server edited file

        . On the NTP daemon configuration file
        . Add a log file statement 
        . This will record all NTP server issues into a dedicated log file
        
      Add this command:
      
        logfile /var/log/ntp.log
  
6, After edited NTP server file 

    . Following all configuration steps explained above 
    . Then save your work 
    . Close ntp.conf file. 
### This complete the NTP setup for Kerberos server side, 
All the above steps can be configured on Client side also.

