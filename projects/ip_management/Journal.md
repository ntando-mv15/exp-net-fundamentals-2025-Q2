# IP Management (Windows)

Notes:

We RDP into the Window's server, and check how our network connections were setup.

With the Windows UI, under `Network Connections`, you can find the Network interfaces attached the server.

- Visible to the eye, are 2 ethernet connections as we configured. 

[Add screenshot]

We used the command prompt to see how we can check our network connections using the CLI.

We ran the command `ipconfig` to get the IP configurations.

## **Understanding `ipconfig` our Windows EC2 Instance** 

The command used to check networking connections, and thus IP configurations in Windows is `ipconfig`.

Upon running this command, these are the thing we noted:


## **1\. Active Interfaces**

We observed multiple blocks like:

    `Ethernet adapter Ethernet0:`

    `Ethernet adapter Ethernet1:`
        

- Each block corresponds to a **network interface (ENI)**.

</br>

For each network interface, we observed:

    `Ethernet adapter Ethernet0:`

    `Connection-specific DNS Suffix  . :`

    `IPv4 Address. . . . . . . . . . . : 10.0.1.23`

    `Subnet Mask . . . . . . . . . . . : 255.255.255.0`

    `Default Gateway . . . . . . . . . : 10.0.1.1`



## 2\. **What Each Line Means**

### `IPv4 Address: 10.0.1.23`

* This is our Window's server's **private IP address**.

* It’s how our Window's server's is known **inside AWS only**.


* The internet **does not see this** address.

  ---

###  `Subnet Mask: 255.255.255.0`

* This defines **how big the network is**.

* In this case, all machines with addresses like `10.0.1.x` are part of the same group.

  So our Window's server's can talk to others from:

   10.0.1.1  →  10.0.1.254

* This is controlled by the **CIDR block** (in AWS, e.g. `10.0.1.0/24`).

  ---

### `Default Gateway: 10.0.1.1`

* This is like the **front door** your EC2 uses to leave home.

* If your EC2 wants to talk to something **outside the subnet** or to the **internet**, it sends traffic to this IP.

* The gateway handles delivery beyond your neighborhood.



## 3. The Elastic IP 

In our **AWS Console**, we attached:

Private: 10.0.1.23

Public: 3.90.21.123

Here’s the important part:

🔸 The Elastic IP **does not show up in `ipconfig`**  
 🔹 AWS handles the mapping behind the scenes

So when someone visits:

http://3.90.21.123

➡ They reach our server (`10.0.1.23`).



## 4. **Other Configurations to Note**

Check DHCP and DNS Settings:

* **DHCP Enabled** – This is for if you'd want your IP to be dynamically assigned.  
* **DNS Servers** – Lists which servers your instance will use to resolve domain names.


</br>

</br>

</br>

---
# IP Management (Linux)

- We used the command prompt to see how we can check our network connections using the CLI.

- Different Linux flavours have different networking tools.
- `ifconfig` is the same as `ipconfig` (Windows) for Linux, but it is deprecated.  
- Now, most people use `ip addr` or `ip a`to check network connections. 




## **Understanding `ip addr` on our Linux Ubuntu EC2 Instance** 

We ran the command `ip addr` to get **all network interfaces** and their IPs.

Upon running this command, these are the thing we noted:

## **1\. Active Interfaces**

Similarly, we observed multiple blocks. Each block:

    ```
    2: eth0: \<BROADCAST,MULTICAST,UP,LOWER\_UP\> mtu 9001  
        inet 10.0.1.23/24 brd 10.0.1.255 scope global dynamic eth0  
        valid\_lft 3153sec preferred\_lft 3153sec

    ```

## 2\. **What Each Line Means**

### `eth0`:

* This is the **name of the network interface**.

* Usually `eth0` is the **main one** for EC2 instances.

* Think of this like the **Ethernet port** on your virtual machine.

---

### `inet 10.0.1.23/24`

* This is the **private IP address** our Linux server, just like in Windows.

   
  * `10.0.1.23` \= Linux server's **private IP**.

  * `/24` \= The **subnet mask**. It means `255.255.255.0` (like before\!).

--- 

### `scope global dynamic`

In simple terms, this tells us that the IP is usable and was probably assigned by DHCP server (dynamic).

--- 
## **The Elastic IP**

Just like in Windows:

- You **won’t** see your **Elastic IP** in `ip addr`\!

* You **only see the private IP** here.

* The **Elastic IP** is shown in the **AWS Console**.

* AWS automatically connects the **Elastic IP (public)** to your **private IP (like 10.0.1.23)** behind the scenes.

