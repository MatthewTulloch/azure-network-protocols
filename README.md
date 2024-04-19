<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04



<h2>Actions and Observations</h2>




First I set up 2 VMs (Windows and Ubuntu), downloaded Wireshark inside the VN, and made sure ICMP traffic was functioning. After confirming, I then went to start pinging the Ubuntu VM. Then after that, I pinged google.


![image](https://github.com/MatthewTulloch/azure-network-protocols/assets/165750459/3b67850d-0317-49e8-ac12-a259ab5f37b7)


I then went inside the network rules and denied ICMP traffic from being transfered (it says allowed here in the title, however inside the rules I said deny). 

![image](https://github.com/MatthewTulloch/azure-network-protocols/assets/165750459/730a33ff-6086-4401-84ba-22c47928c44a)



![image](https://github.com/MatthewTulloch/azure-network-protocols/assets/165750459/b84708f6-bc44-452e-a020-d403c9fd555f)

I then reallowed ICMP traffic and went to the next step of inspecting protocols. 

Next I will SSH into the ubuntu machine and start making wireshark filter for SSH. We can see the packets sending. 

![image](https://github.com/MatthewTulloch/azure-network-protocols/assets/165750459/2153bb5e-8350-43e0-98c1-d4f3f9c84932)


Next I filter by DNS and nslookup google.com and disney.com in order to find both. 

![image](https://github.com/MatthewTulloch/azure-network-protocols/assets/165750459/d69b0fe9-7f0a-45ea-9002-68e429f2531d)



Lastly I filter for RDP traffic. When entering tcp.port==3389 traffic is spammed non stop because we are using Remote Desktopto connect to our VM, which is why it is non-stop spamming when entered. 


![image](https://github.com/MatthewTulloch/azure-network-protocols/assets/165750459/fc839f78-d9ba-4956-91d8-2b554b317bc2)


