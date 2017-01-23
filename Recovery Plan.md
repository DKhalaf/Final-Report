Recovery documentation


Project network

Group 5
	

Autumn 2016















 
![](https://cloud.githubusercontent.com/assets/22467856/22125747/356cbf06-de95-11e6-9eef-291cfa2a58ec.jpg)

Lillebaelt Academy of
University of applied sciences


IT Technology



Authors:
Milan Vince: mila1025@edu.eal.dk

Kevin Herhold Larsen: kevi2901@edu.eal.dk

Rickie Ljungberg: rick0118@edu.eal.dk

Michal Skórczewski: mich74p0@edu.eal.dk


 
1.	Introduction

The document describes the steps how to create “Project Network” which has:

1 client 
2 routers (internal + external)
2 servers (WEB- and DNS server)
![](https://cloud.githubusercontent.com/assets/22467856/22183844/82c8ec0a-e0c7-11e6-96f6-4b7529507425.png)
You will not be able to follow the guideline if you don’t have installed: 
VMware workstation Pro 12 click on the link to get to the homepage and start download by click on downloads on the left side, and choose your OS.

 
 
2.	Overview

•	Files which are needed
•	Level 3 Diagram
•	Vmware booting problems with the routers
•	How to create virtual machines and install
•	Basic configuration of the routers 
•	Installment of the devices (e.x Web Server)
•	Setting up DHCP 
•	Setting up SSH for Server 
•	Sources
•	Check your DNS server
•	External Router Config
•	Configuring the virtual machines







3.	Files which are needed

In these section the plan shows which sources are needed to make the recover:

•	Router: JunOS SRX VMWare virtual machine OVF 
(For EAL students, login Fronter, go in the data communication folder, go in folder called software and click on the arrow down left beside the filename and download)

•	Router: JunOS SRX VMWare virtual machine VMDK 
(same as the previous file)

•	Server: Debian net installer ISO (download)

•	Client: Ubuntu 16.04.1 LTS (Client) (download)

•	Ext. Router.conf file


 
4.	Layer 3 Diagram

This level 3 diagram show the solution and giving a point of view how will the Topology looks like:

![](https://cloud.githubusercontent.com/assets/22467856/22185253/613c4332-e0e2-11e6-9f62-37b9cbf41d49.png)


 
5.	How to create virtual machines 

When you have your VMware up and running you will do following to install a virtual machine, which can be any devices:

1.	When the program is running you will create a virtual machine, by pressing on that box you will get this window

![](https://cloud.githubusercontent.com/assets/22467856/22185294/34f2d8d0-e0e3-11e6-9fd0-742162888f7e.PNG)


 
2.	Afterwards you will press next and now you have to choose the location to your ISO file

![](https://cloud.githubusercontent.com/assets/22467856/22185314/9ef97db0-e0e3-11e6-8dce-57d73903f3f9.PNG)

it’s common to have it in your download folder. 

3.	Now you want to name your machine

![](https://cloud.githubusercontent.com/assets/22467856/22185331/f18aa61c-e0e3-11e6-8856-7e885587906b.PNG)
 

4.	Choose amount of diskspace is you allow the machine to use 

 
5.	Here you have you have to press on the customize hardware button, and setup what how much memory you want the machine to run with.

![](https://cloud.githubusercontent.com/assets/22467856/22185502/4692fc4c-e0e7-11e6-94ee-3dfb4f9f7b05.PNG)
-	be careful not to give the machine too much power if your machine cant handle it!



6.	Finish, repeat the steps from 1 to 5 for the other devices you want to implement in your topology.
 





5.1 Vmware booting problems with the routers

here is a small guide what to do then SRX router does not want to start.

![](https://cloud.githubusercontent.com/assets/22467856/22185515/a3102652-e0e7-11e6-8760-dd05df905a04.PNG)
 
To start with you will setup your router by doing the advanced option,
and after doing the recommended settings you follow the small guide below.


1.	Open your settings in vmware srx:

![](https://cloud.githubusercontent.com/assets/22467856/22185522/d1b1220e-e0e7-11e6-992b-3148cbafe987.png)

2.	If you do not have any serial ports click to: 









3.	Scroll down until add Serial port and click to ”Next >”

![](https://cloud.githubusercontent.com/assets/22467856/22185527/f646c4a2-e0e7-11e6-8417-da047dfc58b9.png) 

4.	Select”Output to file”

![](https://cloud.githubusercontent.com/assets/22467856/22185537/40fc5ea8-e0e8-11e6-9bb7-09e105f525ba.png)
 




5.	When you need to add your file location, write”test”.

![](https://cloud.githubusercontent.com/assets/22467856/22185557/8a9d74fc-e0e8-11e6-80fa-fd696f4bca63.png) 

6.	 There he goes if you have everything done it should show the following:

![](https://cloud.githubusercontent.com/assets/22467856/22185575/bfe48b8c-e0e8-11e6-837f-73d341674f5a.png)


7.	 Finally, you just check your Router is booting as well:

![](https://cloud.githubusercontent.com/assets/22467856/22185596/02a63754-e0e9-11e6-9d97-5e5614722b76.png) 


 
6.	Basic configuration of the routers
The router has some general setup, like giving it a name and password. First you start with login on the internal router, with “root login”.

![](https://cloud.githubusercontent.com/assets/22467856/22185610/3e0095e2-e0e9-11e6-977a-2f7d6660211c.png)

Then you want to make your own password by go in the edit mode by typing:”cli”

![](https://cloud.githubusercontent.com/assets/22467856/22185619/6172d8aa-e0e9-11e6-8c6d-8aee6e690ae6.png)
 
Now you want to set the hostname for the router.

![](https://cloud.githubusercontent.com/assets/22467856/22185635/b16a403c-e0e9-11e6-824d-18ebdfaf3e2a.PNG)

Note: how the router host name now has become a part of the routers prompt.



Next step is to setup the interfaces on your router by typing the following lines.

![](https://cloud.githubusercontent.com/assets/22467856/22185647/d38d8bb0-e0e9-11e6-8624-d1fff99ff90b.png)




Type then: “show interfaces” to see what interfaces you have now.

![](https://cloud.githubusercontent.com/assets/22467856/22185653/ffebc140-e0e9-11e6-9789-a4a4230f4c29.png)

-------------------------------------------------------------------------------------------------------------

The external router use the same steps but in this case the topology only needs 1 interface for the WEB-server therefore should the last step only be: 

![](https://cloud.githubusercontent.com/assets/22467856/22185664/214f9b72-e0ea-11e6-9edd-695005b75171.png) 
 

7.	Installment of the devices
The devices being described here is the client and the servers. 


7.1	Client

Now you simply install the Client double clicking on the machine and you will just follow the steps which the guide in the disk will ask you to do.
 Please don’t install more devices at once, because that could overheat your pc.


note: remember the passwords!

![](https://cloud.githubusercontent.com/assets/22467856/22185700/a1e60dfc-e0ea-11e6-8105-81627c1d99c0.png)

7.2	WEB server
Now you run the disk like before, and following the steps on the disk itself.

![](https://cloud.githubusercontent.com/assets/22467856/22185727/0b2d135a-e0eb-11e6-9a64-13d5a1ebebe0.png)
 

When you are setup the different servers you must name the servers different to not make any confusion. 

![](https://cloud.githubusercontent.com/assets/22467856/22185735/3642cda0-e0eb-11e6-88f4-eae180e0e2ca.png) 

Under setup on the WEB server you should apply SSH which helps you controlling the devices from the client later in the configuration.
7.3	DNS server

![](https://cloud.githubusercontent.com/assets/22467856/22185762/89444178-e0eb-11e6-882f-7e5234eddbf8.png)

Yet again you will install the server by the disk but, when you meet the section with packages to install you must stop and don’t apply anything. Because you will be able to install the correct things later.

 
8.	Configure Debian Webserver

After you launch your WEB or DNS server it will ask you for a login. The Login is “root” , and the password you typed in the setup.

![](https://cloud.githubusercontent.com/assets/22467856/22185814/bfb46f98-e0ec-11e6-8422-93bf85c85d78.png)
 


Type: “ifconfig”

![](https://cloud.githubusercontent.com/assets/22467856/22185840/40dd61d8-e0ed-11e6-9f7f-88162e7a495f.png)

![](https://cloud.githubusercontent.com/assets/22467856/22185862/645e3fe2-e0ed-11e6-92e4-5f649ae4e959.png) 


User can the information about addresses. Check the address you get in browser. (192.168.0.102)

![](https://cloud.githubusercontent.com/assets/22467856/22187112/1ecdfd32-e101-11e6-909a-c9fb91d107d6.png)

If everything went good the user will get this page.


9.	Setting up DHCP 


Login the server and type the following.

![](https://cloud.githubusercontent.com/assets/22467856/22187144/71adfa02-e101-11e6-9d27-2c88ed73ef0d.png)
 


Then type this to install dhcp server.

![](https://cloud.githubusercontent.com/assets/22467856/22187155/94f83e64-e101-11e6-9df3-9a1edac1b35e.png)
 

When the server finishes the installation.

![](https://cloud.githubusercontent.com/assets/22467856/22187163/b47f8620-e101-11e6-812a-64de5148a91a.png)
 

Scroll down here and change subnet, netmask and range addresses as the server has.

![](https://cloud.githubusercontent.com/assets/22467856/22187172/d8f5dfae-e101-11e6-8c1c-38a431c1a4bb.png)

Save it by pressing CTRL + X and restart your device




10.	Configure SSH for Servers


 Type: “apt-get install openssh-server”.
 
![](https://cloud.githubusercontent.com/assets/22467856/22187181/01832b34-e102-11e6-9fd6-89979f955604.png)

![](https://cloud.githubusercontent.com/assets/22467856/22187191/224dbbc2-e102-11e6-8269-de62146060ff.png)

Go into the following folder:” nano /etc/ssh/sshd_config “

 
In this folde you need to look for the following: “PermitRootLogin” and change it to: “yes “ 

![](https://cloud.githubusercontent.com/assets/22467856/22187201/515c234a-e102-11e6-91d3-35e3dd567678.png)

![](https://cloud.githubusercontent.com/assets/22467856/22187203/56c43eda-e102-11e6-99a4-679c1f4c751c.png)

Log out with pressing CTRL + X and save the modifications.

![](https://cloud.githubusercontent.com/assets/22467856/22187210/a023ffb6-e102-11e6-8e13-705be5f30977.png)

11.	Configure the DNS Server with dnsmasq


Type this to get install dnsmasq into your servers.

![](https://cloud.githubusercontent.com/assets/22467856/22187217/b96dd096-e102-11e6-9c8a-150fe9446ce6.png)

Enable dnsmasq

![](https://cloud.githubusercontent.com/assets/22467856/22187235/d4d8462c-e102-11e6-983c-81d2bf02b37d.png)

Type and going to this location:

![](https://cloud.githubusercontent.com/assets/22467856/22187241/f2c454f0-e102-11e6-97b8-5d6ff69f2b23.png)

Change you dhcp-range for the following: 

![](https://cloud.githubusercontent.com/assets/22467856/22187250/12b4383e-e103-11e6-801b-346776e56cf7.png)

DHCP-Option

![](https://cloud.githubusercontent.com/assets/22467856/22187256/2d9f6722-e103-11e6-9ab5-4579e388f7a8.png)

Set your dhcp-option for the following: ( your address)

![](https://cloud.githubusercontent.com/assets/22467856/22187264/5567ce16-e103-11e6-970c-ab83292a3380.png)

![](https://cloud.githubusercontent.com/assets/22467856/22187269/7a58bcbc-e103-11e6-9948-564b36f0f0dd.png)
up
Delete the hashtag(#) from “log-dhcp”

![](https://cloud.githubusercontent.com/assets/22467856/22187274/8f8b9a00-e103-11e6-83c0-8d4563630712.png)

Do the same with “dhcp-authoritative”

![](https://cloud.githubusercontent.com/assets/22467856/22187277/a4483b74-e103-11e6-9105-f034c3142327.png) 

![](https://cloud.githubusercontent.com/assets/22467856/22187279/aa788f94-e103-11e6-8e6c-240a861196e7.png)

Press CTRL + X and save modifications of your folder. 
Sources

Group 7

https://github.com/deadbok/project_network

Juniper vSRX Router Installation

https://fronter.com/eal/links/files.phtml/2080432588$548107012$/1st+Semester/Data+Communication/Literature/Juniper+and+Virtual+Box+GNS+SRX+configuration+V07.pdf


12.	What will be included in this document in next version.
•	Set static ips on the servers


Check your DNS server

In the following steps you will learn how to check if your DNS server working. You will need the following devices to run:
•	Internal Router
•	External Router
•	Client (Ubuntu)
•	DNS

1.	Open terminal in your Client

![](https://cloud.githubusercontent.com/assets/22467856/22187288/e6858e56-e103-11e6-8e72-b3e54f4c2a07.png) 

2.	Type the following: ping router-int-srvlan
(With this command you are trying to get the connection 

![](https://cloud.githubusercontent.com/assets/22467856/22187294/0821f5e0-e104-11e6-8619-effc5ed0de8a.png)

If it is able to ping it means DNS Server is working.


External Router Config
In the following step you will see the Guide how to configure your External router from the beginning:

Step 1:Get SSH for your Ext. Router

#Enter the cli
cli

#Enter edit mode
edit

# Set the root password
set system root-authentication plain-text-password
New Password: type password here
Retype new password: retype password here

# Set the interface to DHCP
set interfaces ge-0/0/3 unit 0 family inet dhcp

# Put the interface in the trusted zone and allow all services
set security zones security-zone trust interfaces ge-0/0/3.0 host-inbound-traffic system-services all

# Allow all protocols
set security zones security-zone trust interfaces ge-0/0/3.0 host-inbound-traffic protocols  all

# Commit the changes
commit
Step 2: Download WinSCP: https://winscp.net/eng/download.php

![](https://cloud.githubusercontent.com/assets/22467856/22187319/9a6416fe-e104-11e6-892f-4102cb691e42.png)

•	Get to install it.
•	Open your External Router in Vmware
•	Type the following: ![](https://cloud.githubusercontent.com/assets/22467856/22187326/acfa62fa-e104-11e6-9eeb-3262ca1edd97.png)
•	Then need to fine Local address of the Ext. Router:
![](https://cloud.githubusercontent.com/assets/22467856/22187334/d33cedac-e104-11e6-99b5-91b7dcea1722.png)
•	Open WinSCP

•	Following on next page
•	 

The program needs to get your Local IP, username and password
![](https://cloud.githubusercontent.com/assets/22467856/22187343/f1d3fb66-e104-11e6-8628-e58da5ff71b5.png)

After Login here is the external router root folder.

![](https://cloud.githubusercontent.com/assets/22467856/22187355/279f8210-e105-11e6-897c-a46a4c256e97.png)

•	Open Notepad++:

Import file: router-ext.conf

![](https://cloud.githubusercontent.com/assets/22467856/22187358/469f3a52-e105-11e6-9235-c602d87ea904.png)

Search on: 

Type into the search:206

Its crucially important to switch that Ip address into your one.

After you have done. (In every single line where’s needed )

Copy your file into your ext. Router //root folder

Overwrite it.


Then go back into Vmware/Ext router
Type in: load override  
![](https://cloud.githubusercontent.com/assets/22467856/22187373/7aa17dc4-e105-11e6-8c77-b15314ee9560.png)
Then commit.
Afterwards you can try to ping another router and Let’s see if it is working or not.


13.	Configuring the virtual machines


To connect the devices together you need click right to your servers, routers or your client, open the settings.

![](https://cloud.githubusercontent.com/assets/22467856/22187380/9c335930-e105-11e6-9f0f-73a7c11ca79a.png)

Open LAN Segments:
Add your Globan LAN Segments.
![](https://cloud.githubusercontent.com/assets/22467856/22187398/d9d7ed96-e105-11e6-8d30-9984e45f4b93.png) 


Add your SVRLAN,USRLAN and DMZ and the Connection of the Routers.

![](https://cloud.githubusercontent.com/assets/22467856/22187404/f771b65c-e105-11e6-8c42-33d1382943d1.png)
![](https://cloud.githubusercontent.com/assets/22467856/22187413/1e291b6e-e106-11e6-81d4-b044c2c338e5.png)

Change your Network Adapter from NAT to LAN Segment. (It depends on your server,router or the client)
(See the connections in our Topology)
![](https://cloud.githubusercontent.com/assets/22467856/22187419/454c00ee-e106-11e6-8e5f-7d21d81dc998.png)

Open your Servers and Routers
![](https://cloud.githubusercontent.com/assets/22467856/22187429/612ae6cc-e106-11e6-95d5-a71a1e715ca7.png)

Ping your DNS Server to check the quality of connection.
![](https://cloud.githubusercontent.com/assets/22467856/22187437/822e45bc-e106-11e6-9afc-f9b13b922fe6.png)


Check your IP address by type the following: ifconfig.
![](https://cloud.githubusercontent.com/assets/22467856/22187443/a06f273a-e106-11e6-9b59-4a50674c37c8.png)


Than try to ping it inside your browser:
![](https://cloud.githubusercontent.com/assets/22467856/22187444/a56f3dba-e106-11e6-8e65-2dce22d74663.png)


Set up username and password for your router

At week 51 we were take part with some presentation, and it went well. If you don’t remember how to setup usrname and password here is one small guide:
1.	Log in to the switch with existing user  or default user (root with no password)  and enter configuration mode:  
root@switch> configure 
[edit] 
root@switch# 

The prompt in brackets ([edit]), also known as a banner, shows that you are in configuration edit mode, at the top of the hierarchy. 
2.	Change to the [edit system login] section of the configuration:    
[edit] 
root@host# edit system login 
[edit system login] 
root@switch#  

The prompt in brackets changes to [edit system login] to show you are at a new level in the hierarchy. 
3.	Now add a new user account:
[edit system login] 
root@switch# edit user michael  

This example adds an account michael, but you can use any account name.
4.	Configure a full name for the account. If the name includes spaces, enclose the entire name in quotation marks ( " " ): 
[edit system login user michael] 
root@switch# set full-name "Michael Mike" 


5.	Configure an account class. The account class sets the user access privileges for the account. 
[edit system login user michael] 
root@switch# set class super-user 

The following access privileges are available for the account 
operator        permissions [ clear network reset trace view ]
read-only       permissions [ view ]
super-user      permissions [ all ]
unauthorized    permissions [ none ]
6.	Configure an authentication method and password for the account: 
[edit system login user michael] 
root@switch# set authentication plain-text-password 
New password:
Retype new password: 

When the new password prompt appears, enter a clear-text password that the system will encrypt, and then confirm the new password.
7.	Commit the configuration: 
[edit system login user michael] 
root@switch# commit 
commit complete 

Configuration changes are not activated until you commit the configuration. If the commit is successful, a commit complete message appears.
8.	Return to the top level of the configuration, and then exit:  
[edit system login user michael] 
root@switch# top 
[edit] 
root@switch# exit 
Exiting configuration mode 
9.	Log out of the switch: 
root@switch> exit 
% logout Connection closed. 


10.	To test your changes, log back in with the user account and password you just configured: 
login: michael
Password: <password> 
--- JUNOS 9.0-R1.1 built 2008-01-15 22:42:19 UTC 
michael@switch> 

When you log in, you should see the new username at the command prompt.




Moving forward to VPN:
Back to School we had a meeting and decided to get IPSEC and a VPN connection with our choosed group, which is Group 7. Early stages we tried to do on the internal router, a week later that’s change for the external, that guy makes mach more sense for IPSEC. The following diagram may will give you more clear:

                                        Group 5                                                  Group 7
![](https://cloud.githubusercontent.com/assets/22467856/22204385/038c7b2c-e172-11e6-9626-7c17faa47ded.png)


 

•	For the first IPSEC: 
IPsec (Internet Protocol Security) is a framework for a set of protocols for security at the network or packet processing layer of network communication. With other words: IPSEC gives you the protection to sending packages in your VPN connection.





Here is one guide:
SRX1

[edit]
fridim@srx-1# edit interfaces

[edit interfaces]
fridim@srx-1# set st0 unit 0 family inet address 192.168.100.1/30
fridim@srx-1# top edit security zones

[edit security zones]
fridim@srx-1# set security-zone untrust interfaces st0.0
fridim@srx-1# set security-zone untrust interfaces st0.0 host-inbound-traffic system-services ike
fridim@srx-1# top edit security ike

[edit security ike] 
fridim@srx-1# set proposal phase1 authentication-method pre-shared-keys
fridim@srx-1# set proposal phase1 dh-group group2
fridim@srx-1# set proposal phase1 authentication-algorithm md5
fridim@srx-1# set proposal phase1 encryption-algorithm 3des-cbc
fridim@srx-1# set proposal phase1 lifetime-seconds 86400
fridim@srx-1# set policy phase1-policy mode main
fridim@srx-1# set policy phase1-policy proposals phase1
fridim@srx-1# set policy phase1-policy pre-shared-key ascii-text juniper
fridim@srx-1# set gateway phase1-gateway ike-policy phase1-policy
fridim@srx-1# set gateway phase1-gateway address 20.20.20.2
fridim@srx-1# set gateway phase1-gateway dead-peer-detection interval 20
fridim@srx-1# set gateway phase1-gateway dead-peer-detection threshold 5
fridim@srx-1# set gateway phase1-gateway external-interface ge-0/0/0.0
fridim@srx-1# top edit security ipsec

[edit security ipsec]
fridim@srx-1# set proposal phase2 protocol esp
fridim@srx-1# set proposal phase2 authentication-algorithm hmac-md5-96
fridim@srx-1# set proposal phase2 encryption-algorithm 3des-cbc
fridim@srx-1# set proposal phase2 lifetime-seconds 3200
fridim@srx-1# set policy phase2-policy perfect-forward-secrecy keys group2
fridim@srx-1# set policy phase2-policy proposals phase2
fridim@srx-1# set vpn to-remote-SRX bind-interface st0.0
fridim@srx-1# set vpn to-remote-SRX ike gateway phase1-gateway
fridim@srx-1# set vpn to-remote-SRX ike ipsec-policy phase2-policy
fridim@srx-1# set vpn to-remote-SRX establish-tunnels immediately
fridim@srx-1# top edit routing-options

[edit routing-options] 
fridim@srx-1# set static route all next-hop 20.20.20.2
fridim@srx-1# set static route 10.2.2.0/24 next-hop st0.0
fridim@srx-1# top edit security

[edit security] 
fridim@srx-1# set address-book global address network-a 10.1.1.0/24
fridim@srx-1# set address-book global address network-b 10.2.2.0/24
fridim@srx-1# edit policies

[edit security policies] 
fridim@srx-1# set from-zone trust to-zone vpn policy trust-to-vpn match source-address network-a destination-address network-b application any
fridim@srx-1# set from-zone trust to-zone vpn policy trust-to-vpn then permit
fridim@srx-1# set from-zone vpn to-zone trust policy vpn-to-trust match source-address network-b destination-address network-a application any
fridim@srx-1# set from-zone vpn to-zone trust policy vpn-to-trust then permit





SRX2

[edit]
fridim@srx-2# edit interfaces

[edit interfaces]
fridim@srx-2# set st0 unit 0 family inet address 192.168.100.2/30
fridim@srx-2# top edit security zones

[edit security zones]
fridim@srx-2# set security-zone untrust interfaces st0.0
fridim@srx-2# set security-zone untrust interfaces st0.0 host-inbound-traffic system-services ike
fridim@srx-2# top edit security ike

[edit security ike] 
fridim@srx-2# set proposal phase1 authentication-method pre-shared-keys
fridim@srx-2# set proposal phase1 dh-group group2
fridim@srx-2# set proposal phase1 authentication-algorithm md5
fridim@srx-2# set proposal phase1 encryption-algorithm 3des-cbc
fridim@srx-2# set proposal phase1 lifetime-seconds 86400
fridim@srx-2# set policy phase1-policy mode main
fridim@srx-2# set policy phase1-policy proposals phase1
fridim@srx-2# set policy phase1-policy pre-shared-key ascii-text juniper
fridim@srx-2# set gateway phase1-gateway ike-policy phase1-policy
fridim@srx-2# set gateway phase1-gateway address 20.20.20.1
fridim@srx-2# set gateway phase1-gateway dead-peer-detection interval 20
fridim@srx-2# set gateway phase1-gateway dead-peer-detection threshold 5
fridim@srx-2# set gateway phase1-gateway external-interface ge-0/0/0.0
fridim@srx-2# top edit security ipsec

[edit security ipsec]
fridim@srx-2# set proposal phase2 protocol esp
fridim@srx-2# set proposal phase2 authentication-algorithm hmac-md5-96
fridim@srx-2# set proposal phase2 encryption-algorithm 3des-cbc
fridim@srx-2# set proposal phase2 lifetime-seconds 3200
fridim@srx-2# set policy phase2-policy perfect-forward-secrecy keys group2
fridim@srx-2# set policy phase2-policy proposals phase2
fridim@srx-2# set vpn to-remote-SRX bind-interface st0.0
fridim@srx-2# set vpn to-remote-SRX ike gateway phase1-gateway
fridim@srx-2# set vpn to-remote-SRX ike ipsec-policy phase2-policy
fridim@srx-2# set vpn to-remote-SRX establish-tunnels immediately
fridim@srx-2# top edit routing-options

[edit routing-options] 
fridim@srx-2# set static route all next-hop 20.20.20.1
fridim@srx-2# set static route 10.1.1.0/24 next-hop st0.0
fridim@srx-2# top edit security

[edit security] 
fridim@srx-2# set address-book global address network-a 10.1.1.0/24
fridim@srx-2# set address-book global address network-b 10.2.2.0/24
fridim@srx-2# edit policies

[edit security policies] 
fridim@srx-2# set from-zone trust to-zone vpn policy trust-to-vpn match source-address network-b destination-address network-a application any
fridim@srx-2# set from-zone trust to-zone vpn policy trust-to-vpn then permit
fridim@srx-2# set from-zone vpn to-zone trust policy vpn-to-trust match source-address network-a destination-address network-b application any
fridim@srx-2# set from-zone vpn to-zone trust policy vpn-to-trust then permit






1.1	Introduction
The Topology in our project has 2 servers, 2 routers, 1 client, 1 vpn and a guest network. 
Layer 2:
![](https://cloud.githubusercontent.com/assets/22467856/22204430/3d045a28-e172-11e6-8301-bd501a283e6c.png) 
Layer 3:
![](https://cloud.githubusercontent.com/assets/22467856/22204445/52ef0ff4-e172-11e6-90b9-5ba877d58641.png) 



1.2	Description of the devices
2x Juniper vSRX Routers which run Junos V12.1x 47-D15.4 and they must be configured as an internal and an external and each router has 3 interfaces. 

The internal router has 3 interfaces. The ge-0/0/0 is connected to the client, the ge-0/0/1 is connected to the dns server and the ge-0/0/2 is connected to the external router. 

The external router has 3 interfaces. The ge-0/0/0 is connected to the internal router, the ge-0/0/1 is connected to the webserver and the ge-0/0/2 is connected to the vpn tunnel.

The dns server runs Debian (Jessie) it translates the ip’s into names. 

The webserver also runs Debian (Jessie) 

The client runs Ubuntu Desktop 64-bit

The VPN IPsec

1.3	Protocols and Standards

IEEE 802.3: Ethernet standard protocol. A collection of standards which define physical layer and datalink layers mac of Ethernet 
 
SSH: Secure shell is used in tcp/ip computer networks 
 
DHCP: Dynamically distributes network configuration parameters such as ip addresses 
 
DNS: It translates the domain name to an ip address
 
DMZ: Is physical or logical subnet work. The purpose of dmz is to add additional layer of security to lan
 
VPN: It allows the user to create a secure connection to another network over the internet.

1.4	End Result of the project

After configuring each device in our network the client are able to use the internet and also to connect to the guest network and is able to ping every devices in that network. the others groups network. 


