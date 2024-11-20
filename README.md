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

5. Run the VM and mount the 2019 ISO 

   ![Screenshot 2024-11-19 162055](https://github.com/user-attachments/assets/07d9fab7-ec3c-44f3-824a-ed4c40a8d9d4)

6. Once it loads up Start windows setup
  
    ![Screenshot 2024-11-19 162312](https://github.com/user-attachments/assets/488e1b7f-2b65-4a58-8376-37eacc399e28)

7. Inside the VM run Virtualbox Guest Additions found in Files > This PC 
8. Shut down DC VM
9. Start it back up
10. Go into Network Connections
11. Rename Network connections (One is for Internal NIC and the other is the Internet NIC which is connected to the host home router)

    ![Screenshot 2024-11-19 164452](https://github.com/user-attachments/assets/5d6470b8-ab70-4bd7-84a0-b524ee9f5e6d)

12. Configure Internal NIC with IP adress

    ![Screenshot 2024-11-19 165418](https://github.com/user-attachments/assets/6d50d373-c26e-468f-8e8e-9dd45f8e8df5)

13. Rename VM PC

    ![Screenshot 2024-11-19 164507](https://github.com/user-attachments/assets/d78fbea2-8835-4413-8f2f-cb593d42e7a5)

14. Restart
    
## What we've done so far: Created Virtual Machine, Configured Internet Network Interface Card (NIC) and Internal NIC, Configured IP adressing for Internal NIC

15. Head into server manager and into roles and features
16. Select Destination server
17. Install Active Directory Domain Services Software

    ![Screenshot 2024-11-19 170651](https://github.com/user-attachments/assets/cca0a444-b2c4-482a-9afd-c6f73e62768b)

18. Configure Domain Controller

    ![Screenshot 2024-11-19 170938](https://github.com/user-attachments/assets/7c8b2063-6d50-422f-ad2e-89a5c2a76128)

19. Restart
20. One back up head over to Active Directoy Users and Computer, within the windows menu
21. Create an organizational Unit in "mydomain.com" directory (This will be the admins folder)

     ![Screenshot 2024-11-19 172709](https://github.com/user-attachments/assets/78d7add9-9571-442e-8617-c336f201bb80)

22. create new user within the new ADMIN directory

    ![Screenshot 2024-11-19 173026](https://github.com/user-attachments/assets/f44338e2-ffc6-4b89-8122-6061a2fcdcb1)

23. Give new user admin permissions

    ![Screenshot 2024-11-19 173159](https://github.com/user-attachments/assets/ce7ebbdc-763d-4803-a7f4-d28cb9bd8a28)

24. log into new user
25. Add new roles and features
26. Select remote access with routing and install

    ![Screenshot 2024-11-19 175041](https://github.com/user-attachments/assets/73bed18f-c86a-49eb-9ca3-f19ee904aa35)

27. then select tools, routing and remote acess, DC Configure, and install NAT

    ![Screenshot 2024-11-19 175500](https://github.com/user-attachments/assets/bc53a2bc-a79e-47d6-9c55-98f699d9f0d6)

## what we're doing next: set up DHCP on our Domain Controller (this will allow Windows 10 clients to get an IP adress and connect to the internet)

28. Back in Server Manager go to add roles
29. Select DHCP and install

    ![Screenshot 2024-11-19 175914](https://github.com/user-attachments/assets/ae2fd693-654b-4ca9-9bd8-fabcf98ca5cc)

30. Go into tools then DHCP
31. Configure IPv4 and IPv6

    ![Screenshot 2024-11-19 180338](https://github.com/user-attachments/assets/e02a6419-e191-4a58-9854-166c2aa8e8aa)

33. Go back to Server Manager/Domain Controller
34. Click Configure this local server
35. Disable IE Enhanced Security Configuration

## Next we're going to create a bunch of "fake" users using a script from Josh Madakor

36. Downloaded script
37. Open Windows Powershell ISE and Run as administrator
38. Launch Powershell script

    ![Screenshot 2024-11-19 181745](https://github.com/user-attachments/assets/df43c376-c0e4-4c14-9e34-7ea8e7c7702b)

39. In powershell make a new line and type this command Set-ExecutionPolicy Unrestricted (select Yes to all)

    ![Screenshot 2024-11-19 182313](https://github.com/user-attachments/assets/a87ee108-d2a4-4bd4-807c-241f21819f05)

40. Run it

    ![Screenshot 2024-11-19 183518](https://github.com/user-attachments/assets/ebed99bc-27cc-4a5c-bcb8-eebc6e1cbbe7)

41. Refresh Active Directory Domain
42. New User Folder should apear with all the users just created

    ![Screenshot 2024-11-19 183537](https://github.com/user-attachments/assets/e646bbfc-d590-49f8-b633-215960efc633)

43. now you can close this VM
    
## Last step is to create a Windows 10 Virtual Machine to see the client side of Active Directory "CLIENT1"

44. Go back to Virtual Box Create a new Virtual Machine (Windows 10 64bit)

    ![Screenshot 2024-11-19 184255](https://github.com/user-attachments/assets/cfba1bfe-0274-4331-9d4e-0cbca40d4198)

45. Change the VM network adapter to internal
46. Run Vm and Mount Windows 10 ISO from earlier

    ![Screenshot 2024-11-19 184357](https://github.com/user-attachments/assets/ab28cda2-1629-45b1-9ecd-685c6eb09e2d)

47. Set up Windows 10 (windows 10 Pro)
48. Custom install
49. Once you load into Client VM and make sure its connected to internet
50. Rename VM and pair it with domain controller

    ![Screenshot 2024-11-19 190205](https://github.com/user-attachments/assets/02a4608e-9ffd-4a16-a408-611ad79232d9)

51. Restart VM
52. Login via other user and imput one of the accounts we set up earlier

    ![Screenshot 2024-11-19 190723](https://github.com/user-attachments/assets/c5a412ce-a270-452a-a7ac-62e14330bfd5)

53. check "whoami" in cmd center and make sure its one of the created accounts and its within the DC domain

    ![Screenshot 2024-11-19 190951](https://github.com/user-attachments/assets/318612e8-8e1d-45c7-937d-05250044aedb)

54. WE HAVE NOW CREATED A MINI CORPORATE SYTEM!!!!!!!
