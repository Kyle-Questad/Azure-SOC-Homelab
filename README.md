🏠 Azure HomeLab

The Goal of this lab to to demonstrate my understanding of the cloud environment by deploying different VM in and azure subscription and create an NSG for the Virtual Machine with open inbound rules allowing anyone on the Virtual machine acting as a honeypot.

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

