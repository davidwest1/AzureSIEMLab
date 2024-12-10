# Azure SIEM Lab
<h2>Description</h2>
This project consists of a building my own Security Operations Center by deploying a SIEM that monitors and generates alerts for all the virtual machine devices within the home lab.
<br />

<h2>Environments and Utilities</h2>

- <b>Microsoft Azure</b>

<h2>Project Setup</h2>
The first step to the lab is setting up the Azure Environment. I created a Windows 10 virtual machine that was used to monitor RDP events. I also opened up RDP on port: 3389 of the VM to allow for immediate network traffic.
<br />
<img src="https://i.imgur.com/8800Nsp.png" height="80%" width="80% alt="AzureSIEMLab"/>
<img src="https://i.imgur.com/IHybLkp.png" height="80%" width="80% alt="AzureSIEMLab"/> 
<br />
Next I deployed Microsoft Sentinel by utilizing a log analytics workspace under the same resource group that I created the VM in.  
<img src="https://i.imgur.com/ccAI2R3.png" height="80%" width="80% alt="AzureSIEMLab"/>
<br />
Sentinel needs a log analytics space to be deployed in order to monitor security alerts and incidents.
<img src="https://i.imgur.com/P4bWCGA.png" height="80%" width="80% alt="AzureSIEMLab"/>
<br />
I created a Windows Security Events data connector that is used to send VM endpoint logs to the log analytics workspace. 
<img src="https://i.imgur.com/XBu5Y7r.png" height="80%" width="80% alt="AzureSIEMLab"/>
<br />
To go along with this, I added a data collection rule, called "WindowsEventstoSentinel", which pulls events from the VM and sends them to widgets within the Sentinel workspace.
<img src="https://i.imgur.com/2L7Qyfm.png" height="80%" width="80% alt="AzureSIEMLab"/>
<br />
The next step is to define the data. I created a Sentinel rule called "Succesful Local Sign Ins" that would show me all successful non-system sign-ins via RDP. 
<img src="https://i.imgur.com/encOVKR.png" height="80%" width="80% alt="AzureSIEMLab"/>
<img src="https://i.imgur.com/C1oQ9oA.png" height="80%" width="80% alt="AzureSIEMLab"/>
<br />
The rule runs every 5 minutes with will group all events into a single alert. 
<img src="https://i.imgur.com/dwQVB6N.png" height="80%" width="80% alt="AzureSIEMLab"/>
<br />
I observed my newly created rule on the Sentinel Analytics page. 
<img src="https://i.imgur.com/GZm2NeT.png" height="80%" width="80% alt="AzureSIEMLab"/>
<br />
After waiting 5 minutes, I tested the rule was working as expected by signing into the VM via RDP and observing the Sentinel incident get created.
<img src="https://i.imgur.com/w5HdkbE.png" height="80%" width="80% alt="AzureSIEMLab"/>
<img src="https://i.imgur.com/GWbxvYD.png" height="80%" width="80% alt="AzureSIEMLab"/>


