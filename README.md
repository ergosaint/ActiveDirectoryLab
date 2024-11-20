# ACTIVE DIRECTORY HOME LAB

## Objective
[Brief Objective - Remove this afterwards]

The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used
[Bullet Points - Remove this afterwards]

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps
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
40. 


*Ref 1: Network Diagram*
