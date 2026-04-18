# Azure-Honeyspot-Lab
<h1>Create Cloud Virtual Machine</h1>
<br>
<h2> Initial architecture overview</h2>
<br>
<p>Inside Azure Subscription we would want to build:</p>
- Resource Group: a fundamental logical container that holds related resources—such as virtual machines, virtual network, databases, and storage accounts—for an Azure solution.
- Inside the Resource Group, we're going to create a <b>virtual network</b> inside their (VNet), and a <b>virtual machine</b> connect to that VNet. Then log in to that VM and turn off its firewall. 
- Then create a Network Security Group (NSG) which filters inbound and outbound traffic for Azure resources using security rules based on IP address, port, and protocol; and open this thing up completely as well.
<br>
<img width="808" height="304" alt="image" src="https://github.com/user-attachments/assets/c7f52d1d-6ebf-46fd-b96e-34e101e409a9" />
<br>

