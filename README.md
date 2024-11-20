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

   ![Screenshot 2024-11-19 161930](https://github.com/user-attachments/assets/1dfefda8-b396-42a2-a3cd-655cf95917a6)

6. Run the VM and mount the 2019 ISO 

   ![Screenshot 2024-11-19 162055](https://github.com/user-attachments/assets/07d9fab7-ec3c-44f3-824a-ed4c40a8d9d4)

8. Once it loads up Start windows setup
  
    ![Screenshot 2024-11-19 162312](https://github.com/user-attachments/assets/488e1b7f-2b65-4a58-8376-37eacc399e28)

11. Inside the VM run Virtualbox Guest Additions found in Files > This PC 
12. Shut down DC VM
13. Start it back up
14. Go into Network Connections
15. Rename Network connections (One is for Internal NIC and the other is the Internet NIC which is connected to the host home router)

    ![Screenshot 2024-11-19 164452](https://github.com/user-attachments/assets/5d6470b8-ab70-4bd7-84a0-b524ee9f5e6d)

17. Configure Internal NIC with IP adress

    ![Screenshot 2024-11-19 165418](https://github.com/user-attachments/assets/6d50d373-c26e-468f-8e8e-9dd45f8e8df5)

19. Rename VM PC

    ![Screenshot 2024-11-19 164507](https://github.com/user-attachments/assets/d78fbea2-8835-4413-8f2f-cb593d42e7a5)

21. Restart
    
#### What we've done so far: Created Virtual Machine, Configured Internet Network Interface Card (NIC) and Internal NIC, Configured IP adressing for Internal NIC

15. Head into server manager and into roles and features
16. Select Destination server
17. Install Active Directory Domain Services Software

    ![Screenshot 2024-11-19 170651](https://github.com/user-attachments/assets/cca0a444-b2c4-482a-9afd-c6f73e62768b)

19. Configure Domain Controller

    ![Screenshot 2024-11-19 170938](https://github.com/user-attachments/assets/7c8b2063-6d50-422f-ad2e-89a5c2a76128)

21. Restart
22. One back up head over to Active Directoy Users and Computer, within the windows menu
23. Create an organizational Unit in "mydomain.com" directory (This will be the admins folder)

     ![Screenshot 2024-11-19 172709](https://github.com/user-attachments/assets/78d7add9-9571-442e-8617-c336f201bb80)

25. create new user within the new ADMIN directory

    ![Screenshot 2024-11-19 173026](https://github.com/user-attachments/assets/f44338e2-ffc6-4b89-8122-6061a2fcdcb1)

27. Give new user admin permissions

    ![Screenshot 2024-11-19 173159](https://github.com/user-attachments/assets/ce7ebbdc-763d-4803-a7f4-d28cb9bd8a28)

29. log into new user
30. Add new roles and features
31. Select remote access with routing and install
32. then select tools, routing and remote acess, DC Configure, and install NAT
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
