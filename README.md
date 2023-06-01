# nttnetworkproject
Building a Network for a company 
This is what I did for NTT NEtworking project: 

<img width="373" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/8e99b558-95d8-49d1-a3a1-0a8d72436ad5">

Starting with building the network I configured the CLI in the Fortigate Firewall 
The task was: 
Build out the network infrastructure for the small business environment.
The client requested a LAN, Guest, and DMZ network.
Build these networks on a FortiNet firewall (a FortiGate).


## Network Setup 

### Configured the LAN interface using putty 
!<img width="566" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/eee818a2-5f27-4716-a75a-1ad2074ad73a">

!<img width="569" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/bef7c28b-7abc-4011-b3cb-1dc00fb7da78">

### Added a Win10 workstation (all configured through GNS3)
Verified the Win10 workstation has leased a DHCP address from the LAN network.
![image](https://github.com/j0well/nttnetworkproject/assets/126909236/d8fe7efb-6104-41a2-9b78-8ea0f0b25380)

### Ping remote destinations to test LAN, WAN, and DNS network connectivity.
<img width="544" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/8bcb9dbc-92d1-4e69-8d86-d053e6161ee0">

### Connected to the firewall GUI
Task: 
- Set the hostname and timezone.
- Enable the NTP server service. This will allow LAN and DMZ devices to sync time with the firewall.
- Set idle logout to 60 minutes. By default the GUI will auto logout after 5 minutes of inactivity, for the lab environment you should increase this to 60 minutes to avoid having to constantly log back into the GUI.
- Enable auto file system check. This tells the firewall to run a system check during boot up. Enabling this prevents a nagging warning message that pops up during login after an unclean shutdown (powerloss/forced reboot/etc). Instead of sending a warning message, the firewall checks the system itself. In a production environment you might leave this 
disabled if you were concerned about peak performance for boot up.

<img width="584" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/fd7d1ebc-1ace-4b2c-ab3e-bf1c16cf674c">
<img width="568" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/cead080a-03ab-4840-b5b5-26ecea9a95c8">
Updated all the configurations fot DMZ, LAN and WAN policys in the firewall GUI.

#### Domain Setup
Task: Add a Win2012r2 server to the lab workspace.

<img width="531" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/a4641571-1f4a-4ef1-8a3d-7e313735191e">

Changed the address of teh network adapter.
<img width="569" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/a7c018ca-5c11-4c18-ae01-c0996de6639d">
<img width="249" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/705b1386-7336-4ed8-b8e5-3827b9c21ffb">

After the configuration the servers are now connected to the internet. Pinged all destionations, LAN, WAN, and DNS.

I needed to set and sycn all interace timezones on the firewall
<img width="250" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/4b2ff324-04b4-45ef-90a0-69b6cf5b9b63">

Updated the domain controller name.
<img width="568" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/31608552-00ce-46b3-9277-bac278848a8f">

### Install Active Directory
Changed DC name. 
<img width="312" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/b586be4b-9898-40ad-a6ad-36f7e136a940">

<img width="448" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/5a627a9e-700b-49d5-932b-e8dc446b9fa6">

Added myself and team to Active Directory Users and Computers.

<img width="504" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/2256c8a7-ce4e-41e8-84cd-3cd9f6358d6a">

Added myself and team to Groups.

<img width="508" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/6cf08933-6477-4440-9e1f-b2c17ad48952">

### Add Win10 workstation to the domain
 <img width="246" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/a78d9e10-c98a-48bf-a359-5da714a27cd9">
 
Once changes were made verified user and admin log-ins 

Changed the background for all users

<img width="564" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/36dda269-fa4c-4237-a2fd-0b6b8d7b9681">

#### IIS Setup
Task: Build a IIS webserver on a win2012r2 server, and join the server to the domain.
The client has requested the server name be: iis.widgets.localdomain

### Installed the IIS server. 
<img width="361" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/6f0158b9-e456-429f-b9dd-1eed0eab2e92">

Added test page to verify.

<img width="570" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/ee481e6e-334a-4c8a-839f-1c5011f794e0">

<img width="359" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/af9b4065-4e7c-4d4d-b6bd-b5a720f077dc">

#### Lamp Setup
<img width="500" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/586da128-eb7c-46c1-92d5-be7b9c8e86ad">
Task: 
- Build a LAMP webserver on Ubuntu server on the DMZ network.
- The client has requested the server name be: www.widgets.localdomain

#### Prepared Ubuntu Server

![image](https://github.com/j0well/nttnetworkproject/assets/126909236/776ea89d-546f-4eab-9f54-0e70c8b65ef6)
![image](https://github.com/j0well/nttnetworkproject/assets/126909236/8142bed6-8887-46b9-82f0-353c39ad485a)
![image](https://github.com/j0well/nttnetworkproject/assets/126909236/bb1335bd-5955-43da-9914-f4e4ddc0239f)

### Install DokuWiki
Instaled with nano  

<img width="496" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/5b5cbbb0-21fe-4777-8a15-1e9413d8651a">

<img width="495" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/f18f4268-33df-486f-92bd-1d52436524c1">

### Configure DokuWiki

<img width="493" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/98427d36-fe19-4ec5-be34-a0c684cc878a">

Renamed the file.
![image](https://github.com/j0well/nttnetworkproject/assets/126909236/0f31704d-3977-4df5-82f6-a678a0013b54)

Created the Docuwiki page for server informatin!!!
![image](https://github.com/j0well/nttnetworkproject/assets/126909236/7b27b2f2-4a69-4f70-840e-b5e06e163774)
![image](https://github.com/j0well/nttnetworkproject/assets/126909236/7b315d5d-9807-4d17-99d8-e765080e5783)

#### Crated a VIP on the firewall

![image](https://github.com/j0well/nttnetworkproject/assets/126909236/020ca210-7abd-4188-800f-ff10f4952c0b)
![image](https://github.com/j0well/nttnetworkproject/assets/126909236/f70a4507-1b84-4394-8373-0ab6b682f723)

### Install the FTP service

Unfortunatly, I forgot to screen shot this day! But this is the documentation used for the FTP installation  
[Windows SErver 2012 FTP insallation](https://social.technet.microsoft.com/wiki/contents/articles/12364.windows-server-2012-ftp-installation.aspx)

#### Scanned enviornment for Vunerabliities
<img width="702" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/b4acd60a-c655-4299-ac41-6ca76bd043ed">

#### Final Topography after setting up infrastructure! 
<img width="367" alt="image" src="https://github.com/j0well/nttnetworkproject/assets/126909236/3ff2d004-8750-40ca-8f35-db9606b10012">
