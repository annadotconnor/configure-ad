<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Install Active Directory
- Create Admin Account 
- Join VM to Domain Controller
- Setup Remote Desktop for 1000 Non-Administrative Users

<h2>Deployment and Configuration Steps</h2>

<h3>Steps Not Shown</h3>

- 1 Azure VM created with Windows 10 (VM1)
- 1 Azure VM Domain Controller created with Windows Server 2022 (DC1)
- Set Domain Controller IP to static
<br><br>

<p>
<img src="https://i.imgur.com/H3BCnCc.png">
</p>
<p>
We are currently in DC1 (domain controller). This is the Server Manager Dashboard. To begin, we will be using ping tests between the two machines, so we need to enable ICMPv4 traffic.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/0x10h4b.png">
</p>
<p>
Bring up Windows Firewall, click Windows Defender Firewall with Advanced Security.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/45BUMht.png">
</p>
<p>
Once here, click Inbound Rules.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/aUSDQTv.png">
</p>
<p>
We can see the various Inbound Rules listed. Be sure the expand this screen so you can see the Protocol column near the right, this is where we will find our ICMP protocols. 
</p>
<br><br>

<p>
<img src="https://i.imgur.com/28tAxbc.png">
</p>
<p>
You can see the ICMPv4 protocols listed here. Go through and enable all. 
</p>
<br><br>

<p>
<img src="https://i.imgur.com/PDrVcZy.png">
</p>
<p>
Going back to our client VM (VM1), we can now perform a ping test using DC1's private IP address of 10.0.0.4 - As we can see, the ping test was successful, and communication between machines is open.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/5HBtyPN.png">
</p>
<p>
Back over to DC1, we will now install Active Directory on our Domain Controller. Click Add Roles and features.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/F77AxgN.png">
</p>
<p>
Once you reach the Installation Wizard above, click Next until you reach the screen shown below. 
</p>
<br><br>

<p>
<img src="https://i.imgur.com/jxw3xOQ.png">
</p>
<p>
On this screen we need to select Active Directory Domain Services. Once selected, click Next.  
</p>
<br><br>

<p>
<img src="https://i.imgur.com/UIt8icx.png">
</p>
<p>
Click Add Features.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/aKSMGUo.png">
</p>
<p>
Active Directory is ready to be installed, Click Next through the following screens, and finally Install.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/UhLv2nz.png">
</p>
<p>
Once installation completes, click Close.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/OrQylaI.png">
</p>
<p>
Navigate back to Server Manager, and click on the yellow attention icon in the upper right.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/9PsmCfq.png">
</p>
<p>
This is alerting us to complete our Active Directory installation by promoting the server to our Domain Controller. So we will click the link that says "Promote this erver to a domain controller".
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5CfGQvH.png">
</p>
<p>
We will now choose our domain. For this lab you can choose anything, the domain won't be public, and the context will not matter.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/gLQzmGZ.png">
</p>
<p>
We will proceed with sukunasdomain.com - If you get the reference, you're superior. Moving on.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/nCd0ZEt.png">
</p>
<p>
Click Next. On the next screen enter a password. This will not be for login, it is for a Restore Mode which is arbritrary for this lab, but must be completed to continue.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/GZE8LrB.png">
</p>
<p>
The domain name has populated. Click Next.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/8TGmyM3.png">
</p>
<p>
And now the installation is complete and ready for reboot. This will sign us out of our DC1 VM.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/wIs5ddC.png">
</p>
<p>
Heading back to Azure we will grab DC1's public IP address, and sign back into Remote Desktop.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/l80VsD3.png">
</p>
<p>
"labuser" is the generic sign in I created during the Azure VM installation process. We will proceed with resigning into our Domain Controller with the credentials of our new domain. Click More Choices to change the login options.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/S8f2l6S.png">
</p>
<p>
Here we can see we must now include the domain in our login credentials. The password is the same for "labuser", it is not the password we created for Restore Mode.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/IctwRda.png">
</p>
<p>
We are now logged back into DC1. 
</p>
<br><br>


<p>
<img src="https://i.imgur.com/o9Uh1K8.png">
</p>
<p>
On the Server Manager Dashboard navigate to the Tools menu in the upper right, and select Active Directory Users and Computers.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/EWPtLsf.png">
</p>
<p>
This is the Active Directory interface. You can see our domain created is shown on the left. Click on the domain, and expand.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/BmjN7rE.png">
</p>
<p>
We will now create a couple Organizational Units or OUs. Right click the domain, and choose New > Organizational Unit.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/qpqtP8G.png">
</p>
<p>
You don't have to use underscores, but doing so will push your OU to the top of the list and does make things a bit easier to find. We will create an Employees OU and an Admins OU. Once Employees is created, repeat the process and create another for Admins.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/6AXNfcv.png">
</p>
<p>
Right click on the domain, hit refresh, and you'll see the OUs created move to the top of the list. 
</p>
<br><br>


<p>
<img src="https://i.imgur.com/xX3L2rj.png">
</p>
<p>
We will now create an Admin user within our Admin OU. Right click on _ADMINS, select New > User.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/N7dBZUT.png">
</p>
<p>
Go ahead and choose your Admin's name. 
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5JBkwaj.png">
</p>
<p>
Choose a password. Be sure to take this down, we will need it to login with our new admin account.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/eSuPxS6.png">
</p>
<p>
Click Finish.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/lmLJktv.png">
</p>
<p>
So now our user is created, but our OU is simply named ADMINS, and we need to actually assign the user to our domain admins group.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/TilVo7x.png">
</p>
<p>
Right click on the user, go to Properties.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/gUr4AQp.png">
</p>
<p>
Go to the Member Of tab, click Add.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5JZHhWd.png">
</p>
<p>
Type Domain Admins, and click Check Names. Once it is underlined, the group is selected. Click OK.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/e9Pw6x6.png">
</p>
<p>
And now Satoru Gojo is part of our Admins group. We will now logout of our "labuser" account, and log back in with our new admin account.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/VER9sum.png">
</p>
<p>
Once reconnected to the Remote Desktop, the login screen will populate. We will login with our domain and new admin credentials (you will probably need to click Use a different account/More choices, etc like before to choose a different user).
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5IVKLu0.png">
</p>
<p>
And just for transparency I have opened a command window to show we are logged in as our new admin.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/fFB5nUG.png">
</p>
<p>
Going back to Azure, we will be setting VM1's DNS server to DC1's Private IP address. VM1's DNS settings are currently pointing to the Virtual Network. To join VM1 to our domain we need to set the DNS to point to our domain controller. Copy the private IP address.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/zRdk2RJ.png">
</p>
<p>
Heading back over to VM1 in Azure, we will navigate to the Networking panel, and click the Networking Interface link shown above.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/payPZVa.png">
</p>
<p>
Click DNS Servers.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/8HayHh5.png">
</p>
<p>
Click Custom. We will now enter the domain controller's private IP address. Click Save. 
</p>
<br><br>

<p>
<img src="https://i.imgur.com/VsHpxmM.png">
</p>
<p>
Now we need to join our Client VM to our domain. Heading back over to our client VM1 in Azure, we will copy the Public IP address and connect.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/FTB6PKf.png">
</p>
<p>
Using Remote Desktop we will paste this IP in, and click Connect to open VM1.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/RuVny70.png">
</p>
<p>
Now in VM1, we will flush dns and run ipconfig /all to see our DNS server is now pointing to our Domain Controller's private IP.
</p>
<br><br>


<p>
<img src="https://i.imgur.com/qWunAR3.png">
</p>
<p>
And just a quick ping test to make sure everything is still connected, and our VMs are communicating. 
</p>
<br><br>


<p>
<img src="https://i.imgur.com/WTzlv3C.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/iFhONgg.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/yzT1nCT.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/0jUywlG.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/ptKT6ET.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/bGAAxFX.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/qkPUIvp.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/Wlkjhgu.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/DPCZQ9n.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/g0GBzo7.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/EwOfSha.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/FmmtUC9.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/F4tcNBh.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/Ei5Ecga.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/XkQWKbZ.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/BuLEwJt.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/FNmxoSm.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/lu4jBAm.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/4aE4c9e.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/DxVIJOI.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/fw9a257.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/UWo8J7n.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/AzbvM4e.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/wK7O3Bg.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/IHUpSqY.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/wZz6dPY.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>












