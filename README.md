# ACTIVE DIRECTORY HOME LAB

## Objective

This GitHub repository documents the setup and configuration of an Active Directory Lab using VirtualBox. The project simulates a real-world network environment, enabling hands-on exploration of Active Directory (AD) functionalities. It provides an opportunity to practice essential IT tasks like user and domain management, network connectivity, and testing employee experience in a controlled lab setup.

### Skills Learned

- Installing and configuring Active Directory Domain Services (AD DS).
- Creating and managing user accounts, including bulk user creation via PowerShell scripts.
- Setting up and managing virtual machines using VirtualBox.
- Configuring multiple NICs (Internal and Internet) for virtual machines.
- Configuring server roles and features.
- Simulating an employee experience by configuring a client machine to authenticate with the domain controller.

### Tools Used

- VirtualBox: Virtualization platform to host virtual machines.
- Windows Server: Operating system for the Domain Controller.
- Windows Client OS: Operating system for the client-side VM.
- PowerShell: Scripting tool used to automate user account creation.

## Steps
### Creating Domain Controller VM "DC"
1. Downloaded Oracle virtualbox
2. Download windows 10 ISO
3. Download Windows Server 2019 ISO
4. Start by creating new VM we'll use as a domain controller in VirtualBox
5. Mount the 2019 ISO to new DC VM
6. Once it loads up Start windows setup
7. Inside the VM run Virtualbox Guest Additions found in Files > This PC
8. Shut down DC VM
9. Start it back up
10. Go into Network Connections
11. Rename Network connections (One is for Internal NIC and the other is the Internet NIC which is connected to the host home router)
12. Configure Internal NIC with IP adress
13. Rename VM PC
14. Restart
#### What we've done so far: Created Virtual Machine, Configured Internet Network Interface Card (NIC) and Internal NIC, Configured IP adressing for Internal NIC

15. Head into server manager and into roles and features
16. Select Destination server
17. Install Active Directory Domain Services Software
18. Configure Domain Controller
19. Restart
20. One back up head over to Active Directoy Users and Computer, within the windows menu
21. Create an organizational Unit in "mydomain.com" directory
22. create new user within the new organizational unit directory
23. Give new user admin permissions
24. log into new user
25. Add new roles and features
26. Select remote access with routing and install
27. then select tools, routing and remote acess, DC Configure, and install NAT
### what we're doing next: set up DHCP on our Domain Controller (this will allow Windows 10 clients to get an IP adress and connect to the internet)

28. Back in Server Manager go to add roles
29. Select DHCP and install
30. Go into tools then DHCP
31. Configure IPv4 and IPv6
32. Go back to Server Manager/Domain Controller
33. Configure this local server
34. Disabel IE Enhanced Security Configuration
### Next we're going to creat6e a bunch of user using a script from Josh Madakor

35. Downloaded script
36. Open Windows Powershell ISE and Run as administrator
38. Launch Powershell script
39. In powershell make a new line and type this command Set-ExecutionPolicy Unrestricted (select Yes to all)
40. Run it
41. Refresh Active Directory Domain
42. New User Folder should apear with all the users just created
43. now you can close this VM
### Last step is to create a Windows 10 Virtual Machine to see the client side of Active Directory "CLIENT1"

45. Go back to Virtual Box Create a new Virtual Machine (Windows 10 64bit) 
46. Change the network adapter to internal
47. Run Vm and Mount Windows 10 ISO from earlier
48. Set up Windows 10 (windows 10 Pro)
49. Custom install
50. Once you load into Client VM and make sure its connected to internet
51. Rename VM and pair it with domain
52. Restart VM
53. Login via other user and imput one of the accounts we set up earlier
54. check whoami command and make sure its the created account and its within the DC domain
55. WE HAVE NOW CREATED A MINI CORPORATE SYTEM!!!!!!!


*Ref 1: Network Diagram*
