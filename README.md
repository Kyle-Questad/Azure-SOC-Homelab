# 🏠 Azure SOC HomeLab
This project demonstrated a real world azure security environment to demonstrate hands-on experience with virtual machine deployment, network security controls, and SIEM based detection using microsoft sentinel.

The lab focuseds on exposing a Windows Virtual Machine to the internet, applying Netowrk Security Group rules, collecting logs inside a Log Analytics Workspace and analyzing security event to understand how cloud-based threats are detected and investigated in a SOC environment.

## 🏗️ Architecture
In this HomeLab I utilized the following resources:
- Virtual Network (VNet)
- Windows 10 Virtual Machine
- Network Security Group (NSG)
- Log Analytics Workspace
- Microsoft Sentinel (SIEM)
- Sentinel Watchlist
- KQL Query
<img width="811" height="744" alt="Azure-HomeLab drawio" src="https://github.com/user-attachments/assets/5fa5409a-31b5-49d8-a037-b2df1875e4e8" />


## 💻 Set Up
The first step for this project was creating a Resource Group I called RG-1 Inside of this resource group I created the following resources. 
  - Virtual Machine
  - Public IP Address
  - Network Security Group
  - Network Interface
  - Disk
  - Virtual Network

<img width="1905" height="909" alt="image" src="https://github.com/user-attachments/assets/52876011-7dc3-4ebd-8a27-32d3d87c6595" />

## 🔏 Network Security Group
After deploying the virtual machine, the assigned Network Secuirty Group was modified to allow inbound traffic from any source. This was intentiionally configured to simulate an exposed system and observe malicious activity targeting publicly accessible cloud resources.

<img width="1912" height="917" alt="image" src="https://github.com/user-attachments/assets/fe7b1feb-957c-415e-bbf1-a4ecd810c023" />

## 💻 Virtual Machine Creation
After remoting onto the Virtual Machine I turned off all Firewall rules inside of Windows Defender Firewall to allow all traffic to have access to get onto the Virtual Machine. After this I pinged the VM from my local host to make sure I was able to reach it. 

<img width="1781" height="1036" alt="image" src="https://github.com/user-attachments/assets/eb840281-7f62-4d4b-a806-25defab13fa7" />

After Confirmting the VM was running I attempted four failed login attempts on it using the username testtrial and checked the event viewer inside of the VM to confirm the failed log-in attempts were being logged.
<img width="1870" height="1011" alt="image" src="https://github.com/user-attachments/assets/c2961cee-b921-4f5f-a538-37dedb97afeb" />

## 📃 WatchList
I then created a watchlist via sentinal name "geoip" with log information. this watch list contains 55k logs which I will be using as a reference to determine whats happening on my network and use this as a reference to determine my next step going forward.

<img width="1626" height="861" alt="image" src="https://github.com/user-attachments/assets/443cfd5a-63b6-4a7d-80ee-6941315b2c1b" />

## 🏢 Log Analytics Workspace
After creating uploading the Watchlist which holds sample data of of different informaiton I generated a KQL query inside of log analytics workspace which organized this data in a column format.
<img width="1915" height="919" alt="image" src="https://github.com/user-attachments/assets/d21782b9-ea71-4e8c-9d74-0822ca783c76" />


## 🗺️ Attack Map
I then created an attack map which shows a map of were all the attempted attacks are being generated from. I did this by used a predefined JSON query in which it pulled all the watchlist data I had uploaded previously and inserted it on the map based the country, longitude, latitude, IP address etc. to located where the attack was coming from.

<img width="1223" height="700" alt="image" src="https://github.com/user-attachments/assets/941a5f48-009d-4568-9ce1-bc38b8f8d2b3" />


## 🚩 Problems I ran into:

- When creating a windows security event inside of azure I didnt have permision to creat a data collection rule. This was due to azure signing me in with a default account when launching Windows security events. To bypass this issue I granted the default account contributor access granting it permision to make any change in azure.
  
  <img width="1917" height="918" alt="image" src="https://github.com/user-attachments/assets/3acd48c2-0434-4d23-8d86-501ee9031227" />

- I had shut down the VM when creating the data collection rule and this lead to the extension not being applyed to my VM, I had to disassociate the data collection rule via monitor and reassociate it while it was running and the extension was successfully deployed on my VM

<img width="1886" height="915" alt="image" src="https://github.com/user-attachments/assets/42a28f03-3908-401a-8591-4eb1f23fd6cd" />


## Resources Used

https://www.youtube.com/watch?v=g5JL2RIbThM
