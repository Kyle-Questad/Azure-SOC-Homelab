🏠 Azure HomeLab

The Goal of this lab to to demonstrate my understanding of the cloud environment by deploying different VM in and azure subscription and create an NSG for the Virtual Machine with open inbound rules allowing anyone on the Virtual machine acting as a honeypot.
Tool I used
- Network Security Group
- 

-------------------------------------------------------------------------------------------------------------------------
The first step for this project was creating a Resource Group I called RG-1 Inside of this resource group I created the following resources. 
  - Virtual Machine
  - Public IP Address
  - Network Security Group
  - Network Interface
  - Disk
  - Virtual Network

<img width="1905" height="909" alt="image" src="https://github.com/user-attachments/assets/52876011-7dc3-4ebd-8a27-32d3d87c6595" />



----------------------------------------------------------------------------------------------------------------------------
After Creation of the Resource Group and the Virtual Machine inside of it. I edited the NSG group assigned to it to allow inbound traffic from any IP and destination port to be allowed onto the VM. This was because were making the VM into a honeypot.

<img width="1912" height="917" alt="image" src="https://github.com/user-attachments/assets/fe7b1feb-957c-415e-bbf1-a4ecd810c023" />

----------------------------------------------------------------------------------------------------------------------------
After remoting onto the Virtual Machine I turned off all Firewall rules inside of Windows Defender Firewall to allow all traffic to have access to get onto the Virtual Machine. After this I pinged the VM from my local host to make sure I was able to reach it. 

<img width="1781" height="1036" alt="image" src="https://github.com/user-attachments/assets/eb840281-7f62-4d4b-a806-25defab13fa7" />

------------------------------------------------------------------------------------------------------------------------------
After Confirmting the VM was running I attempted four failed login attempts on it using the username testtrial and checked the event viewer inside of the VM to confirm the failed log-in attempts were being logged.
<img width="1870" height="1011" alt="image" src="https://github.com/user-attachments/assets/c2961cee-b921-4f5f-a538-37dedb97afeb" />

Problems I ran into:
- When creating a windows security event inside of azure I didnt have permision to creat a data collection rule. This was due to azure signing me in with a default account when launching Windows security events. To bypass this issue I granted the default account contributor access granting it permision to make any change in azure.
  
  <img width="1917" height="918" alt="image" src="https://github.com/user-attachments/assets/3acd48c2-0434-4d23-8d86-501ee9031227" />

- I had shut down the VM when creating the data collection rule and this lead to the extension not being applyed to my VM, I had to disassociate the data collection rule via monitor and reassociate it while it was running and the extension was successfully deployed on my VM

<img width="1886" height="915" alt="image" src="https://github.com/user-attachments/assets/42a28f03-3908-401a-8591-4eb1f23fd6cd" />
