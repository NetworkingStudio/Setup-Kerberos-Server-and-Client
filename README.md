## Setup-Kerberos-Server-and-Client
Study guide to Kerberos server and Kerberos client

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
    
    
    
  b, after NTP server is installed use this command: 
  
        vim /etc/ntp.conf
    
