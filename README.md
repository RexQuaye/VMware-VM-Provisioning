
<h1>VMware VM Provisioning</h1>

### 📋 Tickets Covered in This Repository

- 🖥️ **Ticket #1** — Provision CentOS 9 VM
- 🗂️ **Ticket #2** — Create vSphere Resource Pool
- 🔁 **Ticket #3** — Migrate VM to Resource Pool
- 🌐 **Ticket #12** — Deploy Webserver from Template
- 📸 **Ticket #32** — VM Snapshots
- 🧠 **Ticket #55** — RAM Upgrade with Pre-Change VM Clone

<br />


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
