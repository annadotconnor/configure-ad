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
Back over to DC1, we will now install Active Directory on our Domain Controller.
</p>
<br><br>

<p>
<img src="https://i.imgur.com/F77AxgN.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/jxw3xOQ.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/UIt8icx.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/aKSMGUo.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/UhLv2nz.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/OrQylaI.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/9PsmCfq.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5CfGQvH.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/gLQzmGZ.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/nCd0ZEt.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/GZE8LrB.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/8TGmyM3.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/P4skHp3.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/wIs5ddC.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/l80VsD3.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/S8f2l6S.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/IctwRda.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/o9Uh1K8.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/EWPtLsf.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/BmjN7rE.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/qpqtP8G.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/6AXNfcv.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/xX3L2rj.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/N7dBZUT.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5JBkwaj.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/eSuPxS6.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/lmLJktv.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/TilVo7x.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/gUr4AQp.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5JZHhWd.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/e9Pw6x6.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/VER9sum.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/5IVKLu0.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/VsHpxmM.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/FTB6PKf.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/SNwiRVb.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/fFB5nUG.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/zRdk2RJ.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/payPZVa.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/8HayHh5.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/ZysnJ2G.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>

<p>
<img src="https://i.imgur.com/pyZGWJk.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/RuVny70.png">
</p>
<p>
Lorem ipsum dolor sit amet
</p>
<br><br>


<p>
<img src="https://i.imgur.com/qWunAR3.png">
</p>
<p>
Lorem ipsum dolor sit amet
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












