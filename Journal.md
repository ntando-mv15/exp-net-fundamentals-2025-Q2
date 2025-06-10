## Day 05 - Windows Firewall Rules

I explored **Windows Firewall** by understanding how it controls network traffic using rules for inbound and outbound connections. On an **AWS Windows Server**, I set up a **Python web server on port 8000**, created an inbound rule to allow traffic, and verified access using the **curl command** from my local machine. Additionally, I had to open **port 8000 in AWS Security Group settings**, ensuring both cloud and host-level firewall rules aligned. This helped me grasp **how firewall rules interact with cloud security settings** and how to configure them to controll access to the network.


## Day 04 - Windows Networking Tools

I’ve explored various Windows networking tools on my Windows server, including **ping**, **tracert**, **nslookup**, **netstat** and **route** to better understand network troubleshooting and configuration. I learned how to analyze each of the command outputs and how I would use them to solve networking related issues. These tools have helped me grasp fundamental networking concepts and practical troubleshooting techniques. 


## Day 03 - Packet Tracer Lab

In this lab, I set up a basic network in Packet Tracer with a **switch**, **router**, **DHCP server**, and **PC**. I configured static IPs for the router and server, enabled the **DHCP service** on the server, and observed how the PC requested and received an IP address automatically. This helped me understand how DHCP works, how devices communicate using **broadcasts**, and how the server responds by assigning IPs. I also saw how tools like `ipconfig renew` help verify IP assignment and troubleshoot network issues.


## Day 02 - IP Management


I observed how to check network connections on both **Windows Server** using `ipconfig` and on **Linux** using `ip addr`. This helped me understand how to view **network interfaces**, see which ones are **active**, check assigned **IP addresses** for each and other important network onfigurations. It gave me a clearer picture of how devices are connected and identified on a network.



## Day 01 - Cloud Environment Setup

I set up a **cloud environment** with a **VPC** serving as a virtual network, a **security group** to manage access, and launched **Windows, Ubuntu, and RedHat servers** with appropriate **network interfaces** that we would use throught the bootcamp. I generated **PEM and PPK keys** for authentication, used **Pageant and PuTTY** and **RDP** for secure access, and assigned **Elastic IPs** to ensure static addressing for my servers. The Windows server acts as the primary host, while other instances are used for testing. Through this process, I reinforced **key networking concepts**, including **basic cloud networking, security rules, SSH authentication, and cloud resource management**. 
