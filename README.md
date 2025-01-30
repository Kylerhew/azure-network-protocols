<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Deploying Active Directory and setting up Domain Controller permissions.  <br />






<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
  

<h2>High-Level Steps</h2>

- Step 1 - Making sure the domain controller is configured properly. 
- Step 2 - Add roles
- Step 3 - Set admin user
- Step 4 - Set member of server. 

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/B4soHS9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
1. First we must add roles and features in the server manager. 
</p>
<br />

<p>
<img src="https://i.imgur.com/Ja3LvuM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. Click next until you get to the roles menu.
</p>
<br />

<p>
<img src="https://i.imgur.com/e2FGAHD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
3. Under Active Directory domain service, add features and click next. In the confirmation window check the box for the restart the server automatically and install.
</p>
<br />

<p>
<img src="https://i.imgur.com/km7kjML.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
4. Now we need to configure dc-1 as the domain controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/T8aKm5F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
5. Next in Deployment Config, add a new forest and name your domain controller. In my case I am using MYDOMAIN.COM
</p>
<br />

<p>
<img src="https://i.imgur.com/AEixQ0E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
6. Now in the domain controlleroptions set and confirm your password.
</p>
<br />

<p>
<img src="https://i.imgur.com/sjxbPL2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
7. In the DNS options uncheck "create DNS delegation"" and click next until you get to prerequisites check and then click install. 
  It is now an actual domain controller and the PC should restart. 
</p>
<br />

<p>
<img src="https://i.imgur.com/4Sl2AhT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
8. Log back into the domain controller using new credentials because you have to attach context that you are now logging into a server. So before it was just labuser, but 
   now it is mydomain.com\labuser. But should have the same password. Make sure you use the right slash (\) not (/) 
</p>
<br />

<p>
<img src="https://i.imgur.com/x7q4xVh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
9. Now back in the domain controller we need to create a domain admin user. Click the following path : 
   Start menu >  Administrative Controls > Active Directory Users and Computers.
</p>
<br />

<p>
<img src="https://i.imgur.com/gHul8qr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
10. In Active Directory Users and Computers we need to create some folders.
    Right click mydomain.com in the left column then over to new , then organizational unit. 
</p>
<br />

<p>
<img src="https://i.imgur.com/ZEMeJGA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
10.A. Make sure it is typed out properly  ( see image) _EMPLOYEES
  Then do this again for _ADMINS
</p>
<br />

<p>
<img src="https://i.imgur.com/ISjK29N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11. To create a new user do the following: 
  In Active Directory Users and Computers open up the _ADMINS folder and right click New > Users
</p>
<br /> 


<p>
<img src="https://i.imgur.com/HBtvVCO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11.A. Then put in the name of the new user and the log in userename, click next and in the next screen set a password and write permissions to the user.
  This user is not the admin yet, in order for that to take place we have  to configure the security group for Jane Doe.
</p>
<br />                                                                                                                                                                                                        


<p>
<img src="https://i.imgur.com/M55w8mI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
11.B. In order to officially make Jane Doe the admin user, right click on Jane Doe user folder inside the _EMPLOYEE folder and select properties. From here select member of and select add. In the prompt write "domain admins" and then check names. 
</p>
<br />                                                                                                                                                                                                        


<p>
<img src="https://i.imgur.com/a0c31Hy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
12. Log out of the Domain controller PC and log back in with the Admin credentials : mydomain.com\jane_admins and password is the same. 
</p>
<br />                                                                                                                                                                                                        


<p>
<img src="https://i.imgur.com/GuilFcq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
13. Next we need to join client 1 to the domain server in order for users to utilize the server.
  Right click the start menu and click stystem, then on the rightyou will se "Rename this PC" click on this  and in the computer name tab click on change and under domain write mydomain.com. It will proceed to ask for admin user credentials, once finished the PC will restart and the client is now attached to the domain controller 
</p>
<br />                                                                                                                                                                                                        

                                                                                                                                               




















































































































































































































