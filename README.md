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
---
<h1>Connect the VM to the log analytics workspace</h1>
<img width="474" height="389" alt="image" src="https://github.com/user-attachments/assets/8ceccb0c-411d-4772-8b55-c82be88a4d7d" />
<br>
<p>In Microsoft Sentinel tab, open the tab Content Management, and access Content Hub</p>
<br>
<img width="807" height="378" alt="image" src="https://github.com/user-attachments/assets/148dabec-4679-4f15-9641-e2b80336279c" />
<br>
<p>Search for Windows Security Events and install it </p>
<br>
<img width="801" height="276" alt="image" src="https://github.com/user-attachments/assets/b1e1ad7f-003a-477b-8363-42be6c7fb15b" />
<br>
<p>Once installed, hit Manage</p>
<br>
<img width="768" height="473" alt="image" src="https://github.com/user-attachments/assets/f1955d4c-ec6d-47ac-acab-38734de83224" />
<br>
<img width="787" height="389" alt="image" src="https://github.com/user-attachments/assets/f5ee4cb3-d3d3-4b51-8700-7bc09bb3f320" />
<br>
<img width="812" height="316" alt="image" src="https://github.com/user-attachments/assets/1b46af10-30fb-4ea1-883d-a078549ae116" />
<br>
<p>Then we need to create a data collection rule to forward all our Windows logs to the Log Analytics Workspace</p>
<br>
<img width="791" height="416" alt="image" src="https://github.com/user-attachments/assets/d778f2d9-507d-4687-a394-9bfddb1a29e5" />
<br>
<img width="788" height="715" alt="image" src="https://github.com/user-attachments/assets/02379cb5-80bf-442a-b45c-d9621570f652" />
<br>
<p>Then in <b>Settings - Extensions</b> we can see <b>AzureMonitorWindowsAgent</b> has been installed</p>
<br>
<img width="1853" height="533" alt="image" src="https://github.com/user-attachments/assets/590ca48b-432b-425e-bc5d-5bea539ca801" />
<br>

<h1>Query logs with KQL</h1>
In Log Analytics Workspace, we should see some logs generated from the VM, to query the logs from our Windows machine, use the <b>SecurityEvent</b> table and run the query
<img width="803" height="358" alt="image" src="https://github.com/user-attachments/assets/9da21356-c170-4919-8399-5f89772cdb7a" />
<br>
<p>KQL(Kusto Qury Language) is a powerful, reda-only language developed by Microsoft for rapidly querying and analysing large volumes of stuctured, semi-structured and unstructured data</p>
<br>
<p>We can also filter down which row and column in table we actually want to retrieve the data from </p>
<img width="820" height="382" alt="image" src="https://github.com/user-attachments/assets/b9b48539-09d3-4570-a446-f42ce07fd4b0" />
<br>

<h1>Mapping IP address</h1>
<p>The basic idea is that we put a list of public IP address ranges, feed it into Sentinel and for each ip from the log, it will try to map into the fed data and pinpoint the attacker's location</p>
<br>
<img width="795" height="377" alt="image" src="https://github.com/user-attachments/assets/5b699f29-57f0-4fad-9dc4-c160e618eeec" />
<br>
<img width="796" height="265" alt="image" src="https://github.com/user-attachments/assets/a09ec9cd-99e3-45c8-9d8a-f2ef1b74a1fc" />
<br>
<p>Then download this [IP mapping list](https://www.youtube.com/redirect?event=comments&redir_token=QUFFLUhqbGpfb1dQcURYUDc0ektVdVZmX2pSc01CbThQQXxBQ3Jtc0ttbmp2MWJaMklKbkVPZ1phZjU5dGdFb3Fnc1NCS2Uxa3hJcm5pelRkSENNUWxXVG1EMDdaY1ZDVndYLURTb1NUUDJZa183Z3l2N1BONXlDb0x0RzlxbG5Od2pPWDBNbUI0X01BRDhULWxQdC1HUi1Ndw&q=https%3A%2F%2Fsacyberrange00.blob.core.windows.net%2Fvm-applications%2Fgeoip-summarized.csv%3Fsp%3Dr%26st%3D2025-05-16T00%3A31%3A16Z%26se%3D2030-01-01T08%3A31%3A16Z%26spr%3Dhttps%26sv%3D2024-11-04%26sr%3Db%26sig%3DtaUGULhhgRiY0BRwEEbhusoh%252BxaIQJWAFwxN2%252FOWWhc%253D) and insert it into the watchlist
</p>
<br>
<img width="814" height="200" alt="image" src="https://github.com/user-attachments/assets/d64b6ac3-a10c-4d80-a81c-8d2de9f574e3" />
<br>
<img width="711" height="334" alt="image" src="https://github.com/user-attachments/assets/0e127c86-4335-4201-b2f9-c9b91845e327" />
<br>

<h1>Create a map in Microsoft Sentinel</h1>
<img width="810" height="457" alt="image" src="https://github.com/user-attachments/assets/c9c81216-34c2-4a4d-b991-1cea2d65bdbe" />
<br>
<img width="756" height="271" alt="image" src="https://github.com/user-attachments/assets/96a5ffbf-647b-4f33-a86d-b0aa65d82190" />
<br>
<img width="728" height="545" alt="image" src="https://github.com/user-attachments/assets/aa58d3bb-0792-4a17-a7da-a2ce3bd4b145" />
<br>

```scss
{
	"type": 3,
	"content": {
	"version": "KqlItem/1.0",
	"query": "let GeoIPDB_FULL = _GetWatchlist(\"geoip\");\nlet WindowsEvents = SecurityEvent;\nWindowsEvents | where EventID == 4625\n| order by TimeGenerated desc\n| evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network)\n| summarize FailureCount = count() by IpAddress, latitude, longitude, cityname, countryname\n| project FailureCount, AttackerIp = IpAddress, latitude, longitude, city = cityname, country = countryname,\nfriendly_location = strcat(cityname, \" (\", countryname, \")\");",
	"size": 3,
	"timeContext": {
		"durationMs": 2592000000
	},
	"queryType": 0,
	"resourceType": "microsoft.operationalinsights/workspaces",
	"visualization": "map",
	"mapSettings": {
		"locInfo": "LatLong",
		"locInfoColumn": "countryname",
		"latitude": "latitude",
		"longitude": "longitude",
		"sizeSettings": "FailureCount",
		"sizeAggregation": "Sum",
		"opacity": 0.8,
		"labelSettings": "friendly_location",
		"legendMetric": "FailureCount",
		"legendAggregation": "Sum",
		"itemColorSettings": {
		"nodeColorField": "FailureCount",
		"colorAggregation": "Sum",
		"type": "heatmap",
		"heatmapPalette": "greenRed"
		}
	}
	},
	"name": "query - 0"
}
```
<br>
<img width="802" height="344" alt="image" src="https://github.com/user-attachments/assets/0b7be32c-4b2f-4c0e-ba38-f02baebe7fdf" />

<br>
<img width="802" height="323" alt="image" src="https://github.com/user-attachments/assets/a7a3a7ea-2d9f-4d70-810e-d8b20a20bedd" />

