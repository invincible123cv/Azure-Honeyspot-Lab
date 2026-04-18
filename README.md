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
<br>
<img width="806" height="493" alt="image" src="https://github.com/user-attachments/assets/c51941ca-1849-44dd-bb66-53c655b1dc7a" />
<br>
<p>Then let's make some changes for the NSG, open it to the Internet</p>
<br>
<img width="809" height="459" alt="image" src="https://github.com/user-attachments/assets/c872ec83-8791-462e-b47b-5486c88931e5" />
<br>
- First create an inbound rule that lets everything to establish itself to the computer
<br>
<img width="711" height="809" alt="image" src="https://github.com/user-attachments/assets/200133f2-c265-4b36-a070-48ba1aa69139" />
<br>
<img width="865" height="342" alt="image" src="https://github.com/user-attachments/assets/a611eec1-4f91-4058-8de2-cc95b4980dba" />
<br>
<p>Then we need to log in to our Windows VM to disable internal firewall as well. In our Windows host machine open <b>RDP</b> and connect through the VM's public IP address
 </p>
 <br>
 <img width="803" height="265" alt="image" src="https://github.com/user-attachments/assets/43ac5308-6f0c-420a-a279-a57e6f74a379" />
<br>
<p>Then we just need to turn off the security setting in each of these tabs</p>
<br>
<img width="800" height="532" alt="image" src="https://github.com/user-attachments/assets/85ee85a6-0389-48b4-906a-dd34286f22d3" />
<br>

---
<h1Viewing raw logs></h1>
<p>The computer logs can we easily accessed by accessing <b>Event Viewer</b> on Windows computer
</p>
<br>
<img width="804" height="463" alt="image" src="https://github.com/user-attachments/assets/5b685d6d-69c4-4572-8006-b41a72ba2ac9" />
<br>
<p>Then what we're going to do next is to forward these logs to Azure, and SIEM and see where the potential attackers might be.</p>
<br>

---
<h1>Create a log analytics workspace</h1>
<img width="801" height="396" alt="image" src="https://github.com/user-attachments/assets/86fe61fa-dbf4-4943-8afd-ed62d3a32499" />
<br>
<p>Then we're going to have to create Microsoft Sentinel instance  (a cloud-native, AI-powered Security Information and Event Management (SIEM) and Security Orchestration, Automated Response (SOAR) solution)</p>
<br>
<img width="787" height="222" alt="image" src="https://github.com/user-attachments/assets/babd6a18-79eb-42fb-9891-8f3056da052a" />
<br>
<img width="803" height="175" alt="image" src="https://github.com/user-attachments/assets/a9ecb1d3-73a0-43a5-b4d6-3764884995ae" />
<br>
<p>Then this will actually link our log analytics workspace to Sentinel SIEM, so we can access the logs from the log repository from our SIEM</p>
<br>
<img width="505" height="412" alt="image" src="https://github.com/user-attachments/assets/6ef70182-2bf7-4e30-9c3d-587f72fda259" />
<br>
