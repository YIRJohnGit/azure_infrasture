# Azure Infrasture Setup

## MZF - S02-L13.1 - CREATING VIRTUAL MACHINE ##

  **Tab 1,** _Basics:-_ Click on the Button <Create Virtual Machine>; Select <Pay-as-you-Go>; Create A Resource Group <Create a New Name>; In Instance Details Session, Provide Virtual Machine Name <vmweb01>; Select the Region <East-US>; Retain the Default Settings in Availability Options < No Infrastructure redundancy required>; Select The Image <Windows Server 2012 R2 Datacenter>; Select the Computer Power Size, <1 vcpu, 3.5 GiB Memory>; Administrator Account Section; IN Administrator Account Section <Username>, <Password>, <Confirm Password>; Inbound Port Rules Section, Select the Radio Button  <Allow Selected Ports>, Select Inbound ports <RDP (Remote Desktop Protocal) (3389)>, Select the Button <Next: Disk>

  **Tab 2,** _Disks:-_ Select the Disk Options, OS Disk Type <Standard HDD>, Retain Rest all Default, Click on the Button <Next: Networking>

  **Tab 3,** _Networking:-_ In Network Interface Section, Virtual Network <(New) Payroll-vnet>, Subnet <(new) default(10.0.0.0/24)>, Public IP <(New) vmweb01>,  NIC Network Security Group <Basic>, Public inbound ports <Allow Selected Ports >, Select inbound ports <RDP>, Accelerated Networking <Off> (The selected VM size does not support accelerated networking (Do transaction faster at networking level)); Select Load Balancing Section, And Set the Radio Button Ticked on <No>, and click on button <Next: Management>

  **Tab 4.** _Management:-_ Go to Monitoring Section, Boot Diagnostics <On>, OS Guest Diagnostic <Off>; Diagnostics Storage Account <payrolldiag555>; In identity Section <Off>; Auto Shutdown, Setthe Time and Time Zone, and Select Notify Before Shutdown <Off> (In On State we can set the email to sent), Backup Section, (Selection of On Will Support Disaster Recovery Vault) and Click on the button <Next: Advance>

  **Tab 5,** _Advanced:-_ Extension, Will Support to install Antivirus or client side applications, Monitor Agent, Cloud Init Section for Linux Virtual Machines <VM>; VM Generation, we can select Gen1 or Gen2; Click on the Button <Next: Tag>

  **Tab 6,** _Tages:-_ It is used for Charging Purposes, Billing Purposes for who owns this machine, and we can Specify as follows:
