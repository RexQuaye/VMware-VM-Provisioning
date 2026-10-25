
<h1>VMware VM Provisioning</h1>

### 📋 Tickets Covered in This Repository

- 🖥️ [**Ticket #1** — Provision CentOS 9 VM](#ticket-1)
- 🗂️ [**Ticket #2** — Create vSphere Resource Pool](#ticket-2)
- 🌐 [**Ticket #12** — Deploy Webserver from Template](#ticket-12)
- 📸 [**Ticket #32** — VM Snapshots](#ticket-32)
- 🧠 [**Ticket #55** — RAM Upgrade with Pre-Change VM Clone](#ticket-55)

<br />


<a name="ticket-1"></a>
<h1>Ticket #1 — Provision CentOS 9 VM</h1>

<h2>Languages and Utilities Used</h2>

- <b>VMware vSphere Client (Web UI)</b>
- <b>vCenter Server</b>
- <b>CentOS 9</b>

<h2>Environments Used</h2>

- <b>VMware vSphere / ESXi virtualization platform</b>
- <b>CentOS 9 Linux (guest OS)</b>
- <b>On-prem lab datacenter (vCenter datacenter: Procore-DC)</b>
<br />
<h2>Project walk-through:</h2>

**Objective:** The Infrastructure Team requested a new CentOS 9 virtual machine to support a new product launch for the Software Development team. The VM had to follow a specific naming convention and resource specification, and the resulting asset needed to be recorded in the AssetTiger inventory system. This ticket was also a learning exercise in provisioning and configuring a Linux server from scratch in a virtualized environment.

**Requirements:**

- VM Name: `dev-app-[initials].procore.prod1`
- Host: `10.1.10.90`
- Storage: `DS-01`
- CPU: 1 vCPU
- Memory: 1 GB
- Hard Disk: 20 GB (Thin Provisioned)
- Network Adapter 1: `YT-Intran-vlan`
- ISO: `/DS-01/ISO Images/CentOS-Stream-9-latest-x86_64-dvd1.iso`
- Hostname set to match the VM name, with the asset (including serial number) added to AssetTiger

<br />
<br />
<br />
<p align="center">
<b>Attaching the CentOS 9 ISO:</b>
<br />
<br />
<img width="886" height="603" alt="ticket 1 select file CentOS" src="https://github.com/user-attachments/assets/4b74b50f-ad02-4081-8952-7342bc1e13c3" />
</p>

<br />
<br />
<br />

<p align="center">
<b>VM configuration review:</b>
<br/>
<img width="1166" height="772" alt="ticket_ 1 _ configure and deploy" src="https://github.com/user-attachments/assets/d73bcc3c-16ac-4871-8b7f-4bc4dbd2a3ea" />
</p>

<br />
<br />
<br />
<p align="center">
<b>Work Added to the Asset Tiger inventory:</b>
<br/>
<img width="1898" height="886" alt="Ticket 1 - asset tiger" src="https://github.com/user-attachments/assets/a442cc60-f716-4a41-a436-1ec7ea45bc8d" />
</p>
<br />
<b><u>Solution:</u></b>  Created the VM in vSphere as `dev-app-rexq.procore.prod1` on host `10.1.10.90`, using datastore `DS-01` for both the VM files and the 20 GB thin-provisioned disk. Configured 1 vCPU, 1 GB RAM, and a single NIC on the `YT-Intran-vlan` network per the requirements, then attached the CentOS Stream 9 ISO from the DS-01 ISO Images folder so the VM could boot directly into the installer. Hostname was set to match the VM name, and the completed asset was logged in AssetTiger with its owner, IP, MAC address, CPU/memory allocation, and OS install source recorded.
<br />
<br />

---

<br />
<br />

<a name="ticket-2"></a>
<h1>Ticket #2 — Create vSphere Resource Pool</h1>

<h2>Languages and Utilities Used</h2>

- <b>VMware vSphere Client (Web UI)</b>
- <b>vCenter Server</b>

<h2>Environments Used</h2>

- <b>VMware vSphere / ESXi virtualization platform</b>
- <b>On-prem lab datacenter (vCenter datacenter: Procore-DC)</b>
<br />
<h2>Project walk-through:</h2>

**Objective:** Practice moving workloads between resource pools to build confidence in VM migration and compute resource balancing within vSphere.

**Requirements:**

- Create a resource pool named `RXQUAYE-CLUSTER` under the active Data Center, host `10.1.10.90`
- Migrate an existing VM into the pool using **Change compute resource only**

<br />
<br />
<br />
<p align="center">
<b>Select storage:</b>
<br />
<br />
<img width="1160" height="759" alt="ticket _2_select storage " src="https://github.com/user-attachments/assets/e90c5050-8146-4801-8b25-d530acee5174" />
</p>

<br />
<br />
<br />
<p align="center">
<b>Selecting New Resource Pool:</b>
<br/>
<img width="725" height="495" alt="Ticket 2 - new resource pool" src="https://github.com/user-attachments/assets/957bf698-3421-4416-be6b-898101b3df77" />
</p>

<br />
<br />
<br />
<p align="center">
<b>Naming the resource pool:</b>
<br/>
<img width="950" height="839" alt="Ticket 2 - edit thhe username then -OK-" src="https://github.com/user-attachments/assets/6c191cce-ccaa-4231-b08a-597f53ced0c5" />
</p>

<br />
<br />
<br />
<p align="center">
<b>RXQUAYE-CLUSTER successfully created:</b>
<br/>
<img width="1155" height="431" alt="Ticket 2 - cluster created" src="https://github.com/user-attachments/assets/a2bf6401-b574-4189-abea-3e24e8cea8c6" />
</p>

<br />
<br />
<br />
<p align="center">
<b>Migrating dev-app-rexq.procore.prod1 to RXQUAYE-CLUSTER:</b>
<br/>
<img width="952" height="444" alt="Ticket 2 - migrate my vm" src="https://github.com/user-attachments/assets/8930c1ea-1dc0-4138-843f-2c969ef25a39" />
</p>

<br />
<br />
<br />
<p align="center">
<b>Migrated dev-app-rexq.procore.prod1 server to RXQUAYE-CLUSTER resource pool:</b>
<br/>
<img width="1193" height="707" alt="Ticket 2 - migrating my vm into RXQUAYE-CLUSTER" src="https://github.com/user-attachments/assets/d8c0ba11-c3af-4465-85b6-c7a24eb6bdcd" />
</p>

<br />
<br />
<br />
<p align="center">
<b>Confirming dev-app-rexq.procore.prod1 is in RXQUAYE-CLUSTER:</b>
<br/>
<img width="1062" height="518" alt="image" src="https://github.com/user-attachments/assets/4b0bf1a9-8282-4d8a-83fc-8290ccfc2741" />

</p>
<br />

<b><u>Solution:</u></b>  In vSphere Client, right-clicked the Data Center object under host `10.1.10.90`, selected **New Resource Pool**, and named it `RXQUAYE-CLUSTER`, leaving default CPU/memory reservation settings in place. Then right-clicked the VM `dev-app-rexq.procore.prod1` and selected **Migrate**, choosing **Change compute resource only**, switched to the Resource Pools view, and selected `RXQUAYE-CLUSTER` as the destination to complete the migration. Verified successful placement by confirming `dev-app-rexq.procore.prod1` appeared correctly nested under `RXQUAYE-CLUSTER` in the Hosts and Clusters inventory tree.




<br />
<br />

---

<br />
<br />

<a name="ticket-12"></a>
<a name="ticket-12"></a>
<h1>Ticket #12 — Deploy Dev Webserver from Template</h1>

<h2>Languages and Utilities Used</h2>

- <b>VMware vSphere Client (Web UI)</b>
- <b>NetworkManager TUI (nmtui)</b>
- <b>FreeIPA client (ipa-client-install)</b>
- <b>NFS / fstab</b>
- <b>Vim, Bash</b>

<h2>Environments Used</h2>

- <b>VMware vSphere / ESXi virtualization platform</b>
- <b>CentOS Linux (guest OS, deployed from a template)</b>
- <b>On-prem lab datacenter (vCenter datacenter: Procore-DC)</b>
<br />
<h2>Project walk-through:</h2>

**Objective:** Enhance Linux system administration skills through virtualization using vSphere by deploying a development web server from a configuration template and updating the server-specific settings.

**Requirements:**

- VM Name: `dev-performance-[initials].procore.prod1`
- Deploy from `NEW-YT-DEV-WEBSERVER-TEMPLATE`
- Static network connection
- `ipa-client` package installed and enrolled
- DNS and NFS mount configuration (per Tickets 8-10)
- Local user `procore` added to the `wheel` group
- Asset inventory updated

<br />
<br />
<br />
<p align="center">
<b>Locating the NEW-YT-DEV-WEBSERVER-TEMPLATE in vSphere:</b>
<br/>
<img width="1287" height="639" alt="Ticket 12 template location" src="https://github.com/user-attachments/assets/419bcf49-af85-49ac-a93e-09402a43be5b" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Deploying a new VM from the template:</b>
<br/>
<img width="1108" height="645" alt="Ticket 12 template build  2" src="https://github.com/user-attachments/assets/704cc4ff-f7aa-47ab-9cef-f02345f2e297" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Setting the hostname to match the VM name:</b>
<br/>
<img width="1229" height="718" alt="Ticket 12 setting host name " src="https://github.com/user-attachments/assets/5b731cb1-7431-49fe-b1f7-19ec2cdd6b07" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Configuring the static IP, gateway, and DNS servers in nmtui:</b>
<br/>
<img width="1041" height="541" alt="image" src="https://github.com/user-attachments/assets/b59b326b-1f77-4677-b97a-a4453ed8dafc" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Enrolling the server as a FreeIPA client:</b>
<br/>
<img width="2215" height="1491" alt="image" src="https://github.com/user-attachments/assets/c3ad487b-fa75-4363-b2a2-45b159a19f7b" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Preparing the DNS entries and NFS share mappings in vi:</b>
<br/>
<img width="901" height="626" alt="image" src="https://github.com/user-attachments/assets/4b2ed4bb-c0fc-4978-b028-3f19ad016a86" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Adding the DNS host entries to /etc/hosts:</b>
<br/>
<img width="1938" height="1630" alt="image" src="https://github.com/user-attachments/assets/250b3c16-faed-4ec4-ac0e-dfc805b521f9" />


</p>

<br />
<br />
<br />
<p align="center">
<b>Creating the NFS mount point directories:</b>
<br/>
<img width="1944" height="977" alt="image" src="https://github.com/user-attachments/assets/5f2494c3-f220-4a49-bc59-6669be169938" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Configuring the NFS shares in /etc/fstab:</b>
<br/>
<img width="1957" height="1053" alt="image" src="https://github.com/user-attachments/assets/2a4b71f3-a772-405f-9643-04a573590929" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Mounting the NFS shares:</b>
<br/>
<img width="2258" height="830" alt="image" src="https://github.com/user-attachments/assets/5d34fd65-06d8-403b-bce6-7094d5ddc538" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Adding the procore user to the wheel group:</b>
<br/>
<img width="2241" height="626" alt="image" src="https://github.com/user-attachments/assets/acd36b62-2032-442c-994e-9ea325b6dd02" />

</p>
<br />

<b><u>Solution:</u></b>  Deployed `dev-performance-rxnq2.procore.prod1` in vSphere from the `NEW-YT-DEV-WEBSERVER-TEMPLATE` template using **New VM from This Template**, customizing the operating system and hardware and powering on after creation. Set the hostname to match the VM name and configured a static IP (`10.1.30.152/23`, gateway `10.1.30.1`, DNS `10.1.15.13` and `10.1.15.15`) through `nmtui` using the values from the IPAM sheet. Installed the `ipa-client` package and enrolled the server in the FreeIPA realm with `ipa-client-install --mkhomedir`. Repeated the DNS host entries in `/etc/hosts` and the NFS setup from Tickets 8-10 by creating the `/nfs/incoming/home`, `/nfs/incoming/vhosts`, and `/nfs/incoming/scripts` mount points, adding the three NFS shares to `/etc/fstab`, and mounting them with `mount -a`. Created the local user `procore`, added it to the `wheel` group, and verified the membership with `id procore`. The completed server was then logged in AssetTiger.




<br />
<br />

---

<br />
<br />

<a name="ticket-32"></a>
<a name="ticket-32"></a>
<h1>Ticket #32 — VM Snapshots</h1>

<h2>Languages and Utilities Used</h2>

- <b>VMware vSphere Client (Web UI)</b>
- <b>vCenter Server</b>
- <b>VM Snapshots / Snapshot Manager</b>

<h2>Environments Used</h2>

- <b>VMware vSphere / ESXi virtualization platform</b>
- <b>CentOS Linux (guest OS)</b>
- <b>On-prem lab datacenter (vCenter datacenter: Procore-DC)</b>
<br />
<h2>Project walk-through:</h2>

**Objective:** Strengthen Linux system administrator expertise through virtualization tasks using vSphere by protecting each server with a recoverable snapshot ahead of planned maintenance.

**Requirements:**

- Create a snapshot of every server ahead of a company-wide infrastructure maintenance window
- Servers: `dev-app`, `dev-performance`, and `stage-web`

<br />
<br />
<br />
<p align="center">
<b>Snapshot confirmed for dev-app-REXQ.procore.prod1:</b>
<br/>
<img width="1858" height="530" alt="image" src="https://github.com/user-attachments/assets/3c3cea42-1b4b-4855-ba38-ae3029e11089" />


</p>

<br />
<br />
<br />
<p align="center">
<b>Snapshot confirmed for dev-performance-RXNQ2.procore.prod1:</b>
<br/>
<img width="1877" height="522" alt="image" src="https://github.com/user-attachments/assets/97c52e4c-bdd6-4b95-8442-fa0dbe1586e7" />


</p>

<br />
<br />
<br />
<p align="center">
<b>Snapshot confirmed for stage-web-rexq3.procore.prod1:</b>
<br/>
<img width="1867" height="568" alt="image" src="https://github.com/user-attachments/assets/d45e742c-bf17-493b-8d4a-6e4e5245ca85" />


</p>
<br />

<b><u>Solution:</u></b>  In vSphere Client, right-clicked each VM (`dev-app-REXQ.procore.prod1`, `dev-performance-RXNQ2.procore.prod1`, and `stage-web-rexq3.procore.prod1`), selected <b>Snapshots → Take Snapshot</b>, and gave each snapshot a name and description. Confirmed the tasks completed in the <b>Recent Tasks</b> panel. After the first snapshot, Snapshot Manager showed none, which was a stale view rather than a failed task. Reopening it through <b>Snapshots → Manage Snapshots</b> displayed it correctly. Verified all three snapshots in Snapshot Manager, each with a "You are here" marker confirming the VM's current state sits on that snapshot.




<br />
<br />

---

<br />
<br />

<a name="ticket-55"></a>
<h1>Ticket #55 — RAM Upgrade with Pre-Change VM Clone</h1>

<h2>Languages and Utilities Used</h2>

- <b>VMware vSphere Client (Web UI)</b>
- <b>vCenter Server</b>
- <b>VM Cloning / Edit Settings</b>

<h2>Environments Used</h2>

- <b>VMware vSphere / ESXi virtualization platform</b>
- <b>CentOS Linux (guest OS)</b>
- <b>On-prem lab datacenter (vCenter datacenter: Procore-DC)</b>
<br />
<h2>Project walk-through:</h2>

**Objective:** Learn how to configure resources of a Linux server in a virtualized environment by increasing a server's memory safely, with a backup clone created before any change.

**Requirements:**

- VM: `dev-app`
- Increase RAM by 500 MB to support increased user demand
- Create a clone of the `dev-app` server before making changes

<br />
<br />
<br />
<p align="center">
<b>Opening the Actions menu for dev-app-REXQ.procore.prod1:</b>
<br/>
<img width="690" height="959" alt="image" src="https://github.com/user-attachments/assets/b6f5cf0c-d95e-4672-9296-340bf5d8f51d" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Selecting Clone → Clone to Virtual Machine:</b>
<br/>
<img width="1113" height="550" alt="image" src="https://github.com/user-attachments/assets/36ef8997-f884-421a-ad7c-d69662b0a9de" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Naming the clone dev-app-rexq-clone1.procore.prod1:</b>
<br/>
<img width="836" height="289" alt="image" src="https://github.com/user-attachments/assets/9e1f38e5-8710-4c58-bdc7-cb5a741f49fb" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Selecting the compute resource (host 10.1.10.90):</b>
<br/>
<img width="763" height="289" alt="image" src="https://github.com/user-attachments/assets/00cad7c7-cd61-4c97-913d-89addfb7701d" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Selecting the DS-01 datastore:</b>
<br/>
<img width="923" height="373" alt="image" src="https://github.com/user-attachments/assets/1aa3894e-8b4f-43fa-8f83-ff3056a90f41" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Selecting the clone options:</b>
<br/>
<img width="801" height="283" alt="image" src="https://github.com/user-attachments/assets/243ce1bd-64e9-423c-8b8c-797872a1c2f8" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Reviewing the clone settings before finishing:</b>
<br/>
<img width="1126" height="739" alt="image" src="https://github.com/user-attachments/assets/3a35c7a6-648c-4d44-ac99-0a65903eb983" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Migrating the clone: Change compute resource only:</b>
<br/>
<img width="797" height="715" alt="image" src="https://github.com/user-attachments/assets/ea6f37f1-c69c-44e1-854b-8dbeaf95c7a2" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Placing the clone in the RXQUAYE-CLUSTER resource pool:</b>
<br/>
<img width="789" height="708" alt="image" src="https://github.com/user-attachments/assets/c6468535-a694-4b9c-ae4f-ef140e7a2f31" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Increasing dev-app memory to 1524 MB in Edit Settings:</b>
<br/>
<img width="906" height="763" alt="image" src="https://github.com/user-attachments/assets/c788d388-6392-45b1-b2a0-b1c5f8aa619a" />

</p>

<br />
<br />
<br />
<p align="center">
<b>Verifying the new memory on the Summary tab:</b>
<br/>
<img width="1926" height="1451" alt="image" src="https://github.com/user-attachments/assets/19dab03d-42dc-4f25-be5c-daa1c01b0f04" />

</p>
<br />

<b><u>Solution:</u></b>  In vSphere Client, right-clicked `dev-app-REXQ.procore.prod1` and selected <b>Clone → Clone to Virtual Machine</b>, naming the clone `dev-app-rexq-clone1.procore.prod1` and placing it on host `10.1.10.90` with datastore `DS-01` and the same disk format as the source, so a safe backup existed before any change. The clone powered on automatically with the same IP address as the original, so I powered it off to avoid a network conflict, then used <b>Migrate → Change compute resource only</b> to place it in the `RXQUAYE-CLUSTER` resource pool. Because memory could not be edited while the VM was running, I powered off `dev-app-REXQ.procore.prod1`, opened <b>Edit Settings</b>, and increased Memory from 1 GB to 1524 MB (+500 MB), correcting an initial entry made in the Reservation field with the unit left on GB. Powered the VM back on and verified the change on the Summary tab, which shows 1.49 GB of memory.



