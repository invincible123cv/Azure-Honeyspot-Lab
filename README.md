# Azure-Honeyspot-Lab
<h1>Create Cloud Virtual Machine</h1>
<h2> Initial architecture overview</h2>
<p>Inside Azure Subscription we would want to build:</p>
- Resource Group: a fundamental logical container that holds related resources—such as virtual machines, virtual network, databases, and storage accounts—for an Azure solution.
- Inside the Resource Group, we're going to create a <b>virtual network</b> inside their (VNet), and a <b>virtual machine</b> connect to that VNet. Then log in to that VM and turn off its firewall. 
- Then create a Network Security Group (NSG) which filters inbound and outbound traffic for Azure resources using security rules based on IP address, port, and protocol; and open this thing up completely as well.
<br>
<img width="808" height="304" alt="image" src="https://github.com/user-attachments/assets/c7f52d1d-6ebf-46fd-b96e-34e101e409a9" />
<br>

<h2>Create Resource Group</h2>
<img width="807" height="351" alt="image" src="https://github.com/user-attachments/assets/97748bdb-e755-4ce1-ab08-520ef07bb932" />
<br>
<img width="810" height="359" alt="image" src="https://github.com/user-attachments/assets/be57611e-f781-404d-b5a3-d28e8a615117" />
<br>
<img width="808" height="163" alt="image" src="https://github.com/user-attachments/assets/c4823075-6181-4a01-820e-d96399008c35" />
<br>
<img width="810" height="370" alt="image" src="https://github.com/user-attachments/assets/3aec10f4-00ba-43ac-b353-0c8da4fbe69b" />
<br>

<h2>Create Virtual network</h2>
<img width="786" height="420" alt="image" src="https://github.com/user-attachments/assets/34b9cca2-b286-44b3-9f0b-22cce82bdde9" />
<br>
<img width="806" height="472" alt="image" src="https://github.com/user-attachments/assets/a217c64c-3fd4-4494-ad87-dcf65f16cf55" />
<br>
<p>And leave the rest of the default configurations as they are</p>
<br>

<h2>Create a VM (a honeypot exposed to the Internet)</h2>
<img width="811" height="319" alt="image" src="https://github.com/user-attachments/assets/a5afe968-405d-4117-9d06-2f474b50ca48" />


