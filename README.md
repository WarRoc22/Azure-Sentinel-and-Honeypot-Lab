# Azure-Sentinel-and-Honeypot-Lab
In this lab I created a honeypot virtual machine and connected it with Microsoft Sentinel. Sentinel then created a map of all the failed login attempts from around the world. For this lab I followed along Josh Madakor: [https://www.youtube.com/watch?v=RoZeVbbZ0o0&list=PLqBeiU46hx1H--SNfTrohTOWeqkK-M2Y0&index=10](url)

The following screenshots is me creating the virtual machine that will be used as the honeypot:
![Honeypot1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/8efcdc9b-c1c9-4114-80f7-0f0dac6911fa)
![Honeypot2](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/152da059-d30c-43be-a50f-b6906617dc5b)
![Honeypot3](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/476cdd90-55c5-4225-b4a8-d61333a1540a)
Setting up the firewall to allow all traffic to go to the virtual machine:
![Honeypot4](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/860523c2-6432-4548-b47a-ea57ef603122)
![Honeypot5](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/f00347ff-99ad-47c9-ae9b-1b7a20bc8cdc)


The following screenshots is me setting up the Log Analytics Workspace. This will allow Sentinel to be able to ingest all event logs from the virtual machine

![LogAnalytics1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/dbf374f7-8a80-4fc3-be97-05b9bae3caca)
![LogAnalytics2](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/018f2315-2e83-4adb-8106-ca288cf6e24b)
![LogAnalytics3](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/31b518c9-208e-47f5-bc3b-c44c8180bae7)
Connecting log Analytics Workspace to the virtual machine
![LogAnalytics4](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/9bcb6c47-0a42-4b7c-a033-1a412800bf0d)


The following screenshot is me creating and adding Sentinel to the workspace I created:
![Sentinel1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/02d0dac2-0c7f-4644-9155-03db9973d4dc)


The following screenshots is me logging onto the virtual machince I created:
![vm1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/c2af1003-8a81-425e-baa8-050e87c9aee2)
![vm2](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/a0d292e8-9cd0-4914-9917-ca02a32606af)
![vm3](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/1d9b4a5c-f7c9-405c-8a80-5d8accaa432c)
I did a failed login attempt so that it would show in the security log:
![vm6](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/a643d9c8-49c3-4389-82d0-2ec01b076f68)
![vm4](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/a6b76fac-2a20-4552-9904-9fb121671ca4)
![vm5](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/b53f5180-b0ab-46a1-9915-010f197cb7a0)


The following screenshots is me pinging the virtual machine:
I tried pinging the virtual machine but was getting Request timed out:
![Pinging1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/adacd732-df02-4ba7-8344-4ceba93106c7)
I turned off the firewall on the virtual machine. I was able to ping the virtual machine:
![Pinging2](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/26ac4d79-263c-4952-9c4d-abe42a67fa47)
![Pinging3](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/c82f8578-a71c-4b9e-b3c2-1f3287811466)
![Pinging4](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/f368ce6d-5055-4613-8ee9-941d8d6f3352)


The following screenshots is the PowerShell script that I ran to be able to export logs from the virtual machine to Sentinel:
![PS1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/1447a091-daca-4a46-9ac9-dbc53c5792ea)
This is the location where the file that keeps failed logins is generated from the PowerShell script
![PS2](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/3814f179-b5e4-4503-be82-1bcd4b87beee)
After Running the PowerShell Script, it now shows my failed login attempt
![PS3](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/6ab78b5c-5ff8-4d7d-9be1-3741a59e6cc7)
The file that was generated from the PowerShell script that will keep the failed login attempts
![PS4](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/147f2006-57e5-49d9-89fd-c12dee85cb87)
I did another failed login attempt to see in PowerShell
![PS5](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/35ec13aa-d5cc-4f18-a65f-b96ecc500c3d)


The following screenshots is the custom log in Log Analytics I created:
For the sample log, I copied all the data from the failed_rpd file in the Virtual Machine. I then pasted the data into an empty notepad log file
![cl1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/11080c73-d7db-44f5-bcc4-de940e7845bc)
![cl2](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/9ea9c160-a5a3-48f9-89f3-3f8a9b3fe7ce)
![cl3](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/031f82a8-9914-4445-86a1-2b64e428b952)
![cl4](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/1502d9d2-f2dc-4639-919b-fc89cad9158e)
![cl5](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/a539ba4f-755b-4205-bb84-bb1c31479c8e)
Ran the following query to see failed RDP logs:
![cl6](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/3ba5ee57-f149-46bb-8536-fd41b7852de4)
Ran the custom log 8 hours later for an updated list of failed login attempts
![cl7](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/c7a2276d-fa3d-43f0-b32c-6546642c699a)


The following screenshots is me setting up the map in Sentinel Workbooks:
![Map1](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/748a3193-1a4e-4f2e-ba6d-d5fca152e86f)
![Map2](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/b03ca328-bdd2-4abe-b382-293f75079f70)
The following is the finished map with the current failed logins from around the world:
![Map3](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/c86b55fa-75e5-4a23-9733-5337d60e67f6)
This is the map 8 hours later with updated login attempts:
![Map4](https://github.com/WarRoc22/Azure-Sentinel-and-Honeypot-Lab/assets/148729293/bb6f0b57-6f71-4000-a0c4-b844244ca643)








