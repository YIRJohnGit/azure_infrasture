# Azure Infrasture Setup

## MZF - S02-L13.1 - Creating Virtual Machine ##

  **Tab 1,** _Basics:-_ 
   Click on the Button < Create Virtual Machine >; 
   Select < Pay-as-you-Go >; 
   Create A Resource Group < Create a New Name >; 
  In Instance Details Session, 
   Provide Virtual Machine Name < vmweb01 >; 
   Select the Region < East-US >; 
   Retain the Default Settings in Availability Options < No Infrastructure redundancy required >; 
   Select The Image < Windows Server 2012 R2 Datacenter >; 
   Select the Computer Power Size, < 1 vcpu, 3.5 GiB Memory >; 
   
   Administrator Account Section; 
    IN Administrator Account Section < rootadmin >, < ^k3A7&^k13J9 >, < ^k3A7&^k13J9 >; 
    
   Inbound Port Rules Section, 
    Select the Radio Button  < Allow Selected Ports >, 
    Select Inbound ports < RDP (Remote Desktop Protocal) (3389) >, 
    Select the Button < Next: Disk >

  **Tab 2,** _Disks:-_ 
  Select the Disk Options, OS Disk Type < Standard HDD >, 
  Retain Rest all Default, Click on the Button < Next: Networking >

  **Tab 3,** _Networking:-_ 
   In Network Interface Section, 
    Virtual Network < (New) Payroll-vnet >, 
    Subnet < (new) default(10.0.0.0/24) >, 
    Public IP < (New) vmweb01 >,  
  
  NIC Network Security Group < Basic >, 
   Public inbound ports < Allow Selected Ports >, 
   Select inbound ports < RDP >, 
   Accelerated Networking < Off > (The selected VM size does not support accelerated networking (Do transaction faster at networking level)); 
   Select Load Balancing Section, And Set the Radio Button Ticked on < No >, and 
   click on button < Next: Management >

  **Tab 4.** _Management:-_ 
  Go to Monitoring Section, Boot Diagnostics < On >, 
   OS Guest Diagnostic < Off >; 
   Diagnostics Storage Account < payrolldiag555 >; 
   In identity Section < Off >; 
   Auto Shutdown, Setthe Time and Time Zone, and Select Notify Before Shutdown < Off > 
   (In On State we can set the email to sent), 
   Backup Section, (Selection of On Will Support Disaster Recovery Vault) and 
   Click on the button < Next: Advance >

  **Tab 5,** _Advanced:-_ 
  Extension, Will Support to install Antivirus or client side applications, Monitor Agent, Cloud Init Section for Linux Virtual Machines < VM >; 
  VM Generation, we can select Gen1 or Gen2; 
  Click on the Button < Next: Tag >

  **Tab 6,** _Tages:-_ 
  It is used for Charging Purposes, Billing Purposes for who owns this machine, and we can Specify as follows:

 ![image](https://user-images.githubusercontent.com/111234771/196573877-759927f6-ed3d-4ef4-80ae-26f06a9b2e6f.png)

 ## MZF - S02-L15.1 - Connecting Vrtual Machine with Remote Desktop ##

  Go to Windows Run Program, type <mstsc (Microsoft Terminal Service Console)> on run command text in put field, Remote Desktop Connection , Ener the Virtual Machin’s  Public IP Address, Updated User ID and Password
 
 _Run Command on Windows_
 ![image](https://user-images.githubusercontent.com/111234771/196572683-97c9736a-33e1-4c92-b7da-4218eecd7b7b.png)
 
 _Result: Connecting to Remote Computers_
 ![image](https://user-images.githubusercontent.com/111234771/196572743-7332f1fa-6a44-485e-a365-36dbd79a6b0d.png)

 _Result: for Login Credential_
 ![image](https://user-images.githubusercontent.com/111234771/196572848-87501e31-28b3-46e3-8e82-193e53c54d7f.png)

 ## MZF - S02-L16.1 - Setting Up for Web Server on Windows Virtual Machine ##

  **Tab 1,** _Basics:-_ Cli
For Windows, Go to Server Manager, Click on the link <Add roles and features> (Such as Active Directory Roles, for Domain Controller, or DNS Server, or DHCP Roles, Now we are going select web server to host web application ); 

 **Tab 1,** _Before Begin_ < Retail all Default Settings >; Click on < Next > Button

 **Tab 2,** _Installation Type:_ Select < Role Based and Feature-based installation > and Click on < Next > Button 

 **Tab 3,** _Server Selection:_ Select the Virtual Machine Available in the List <Microsoft Server 2012, R2 DataCenter>, Click on < Next > button

 **Tab 4,** _Server Roles:_ Tick on the List to Select Web Server (IIS), While Selecting this will ask for Some more dependency in the next Windows and Select Add Features and click the Button <Add Features>,  Click on < Next  > Button in Server Role Table
 
 **Tab 5,** _Features:_ Click < Next > Button with Default Setting

 **Tab 6,** _Web Server Role(IIS):_ Click on <Next> Button; in Click Next in Sub Menu Called Role Serves; Click Next to Move on to Confirmation

 **Tab 7,** _Click <Install> Button_, this will take some Site, and this Machine will become Web Server and Click on < Close > button

_@ Verify:_ Launch the Internet Explorer, and verify the url http://localhost/, and you will get default page and to access the Public IP and need to Open the Port 80/443 and we are learning in Next Video_

 
 
![image](https://user-images.githubusercontent.com/111234771/196573721-fe275b46-6613-442e-9483-2b02fa13d5d0.png)

![image](https://user-images.githubusercontent.com/111234771/196573743-32e8c5a7-8264-4fda-834d-64b8f9871299.png)


 
 ## MZF - S02-L17.1 - Setting Up Public IP Access, Security Group, Inbound Role 80/443 Ports in Azure Portal ##

  _Go to Networking Section form the Main Menu_, 
 **Note:** in this tab, Public IP Address, Private IP Addres, Virtual Network / Subnet and DNS Name and Other Metrics for Performance Purposes;
Setting UP INBOUND role in the Networking Tab, Set the Follwing:
Source < Any > ; Source Port Range < * >; Destination < Any >; Destination Port Range < 80 >; Protocal <Any (TCP/UDP) >; Action < Allow >; Priority < 310 >; Name < port_80 >; Description < Enter Some Description > and Click the < Add > Button

@ Verify the Browser with Public IP Address, and you will be able to access the web site….

 _Note: NEXT WE ARE GOING TO LEARN How to Modify the web site_

 
 ## MZF - S02-L18.1 - Changing the Content of Web Server in Windows Server Machine ##

  Go to , C:/Windows/inetpub/wwwroot folder, and iisstart.html will be the default startup and we can add index.html
Open the index.html and write the content

 
 ![image](https://user-images.githubusercontent.com/111234771/196574681-4d872e8d-d49d-441e-997b-4be0c267b46d.png)

 
  ## MZF - S02-L22.1 - Confifuring Two Subnets on the Same Network in windows Server Machine Using CIDR (CIDR – 192.168.) ##
  ### STEP 1 - GO TO VIRTUAL NETWORKS FROM THE MAIN MENU ###
   Click on to the Add Button or Create Button
   _In Create Virtual Network Tab_
   o	Name < Vnet_Production>
   o	Address Space < 192.168.0.0/16 >(Class C IP Address)  (Specify Class A / B / C and Learn More on the same)
   o	Subscription < Pas-As-You-Go (Free) >
   o	Create a New Resource Group <  Payroll >
   o	Select the Region <  Central US >
   o	Subnet Name < Subnet1 >
   o	Address Range < 192.168.30.0/24 > and retain the rest of to default Setting and Click the Button Create
   Go to Home > Virtual Network > Vnet_Production – Subnets (For Creating 2nd Subnet)
   	Click on the Subnet Button
   o	Name < Subnet2 >
   o	Address Range (CIDR Block) < 192.168.40.0/24 > and retain the rest od the option to default and press ok button

   _Creating a Virtual Machines with the Following Changes in 1st Subnet_
   	Make Sure the VM are on the same Regions, Example : Central US, In Basic Tab
   	In Networking, 
   o	Select Virtual Network < Vnet_Production >
   o	Select Subnet Name < Subnet1 ( 192.168.30.0/24 ) > and retain the default Setting in the Networking Section

   Retain Default Setting Same and Review and Create

   Creating a Virtual Machines with the Following Changes in 2nd Subnet
   	Make Sure the VM are on the same Regions, Example : Central US, In Basic Tab
   	In Networking, 
   o	Select Virtual Network < Vnet_Production >
   o	Select Subnet Name < Subnet1 ( 192.168.40.0/24 ) > and retain the default Setting in the Networking Section

   Retain Default Setting Same and Review and Create
 
   ### STEP 2 – CONFIGURING SUBNETS IN WINDOWS SERVER MACHINES (CIDR – 192.168.) ###
   Open the Remote Desktop of both the Virtual Machines, Start the terminal, and verify the communication
   ipconfig
   ping 196.168.40.4

   ipconfig
   ping 196.168.30.4

 _Inbound Settings_
 ![image](https://user-images.githubusercontent.com/111234771/196624334-6522e899-d83f-457a-aa84-efc3d118bb57.png)

 
