<h1>VMware VM Provisioning</h1>

<h1>Ticket #1 — Provision CentOS 9 VM</h1>

<h2>Languages and Utilities Used</h2>

- <b>VMware vSphere Client (Web UI)</b>
- <b>vCenter Server</b>
- <b>CentOS 9</b>

<h2>Environments Used</h2>

- <b>VMware vSphere / ESXi virtualization platform</b>
- <b>CentOS 9 Linux (guest OS)</b>
- <b>On-prem lab datacenter (vCenter datacenter: Procore-DC)</b>

<h2>Project walk-through:</h2>

**Objective:** Provision a new CentOS 9 virtual machine in vSphere to serve as a dev-app host, configured with the specified compute, storage, and network resources and ready for OS installation.

<p align="center">
VM configuration review: <br/>
<img src="images/ticket-01-vm-review.jpg" height="80%" width="80%" alt="VMware New Virtual Machine wizard, Ready to complete step, showing VM configuration summary"/>
<br />
<br />
Attaching the CentOS 9 ISO: <br/>
<img src="images/ticket-01-iso-select.jpg" height="80%" width="80%" alt="VMware Select File dialog with CentOS9 ISO selected from the DS-01 datastore"/>
</p>

**Solution:** Created the VM through the vSphere "New Virtual Machine" wizard — selected the compute resource and DS-01 datastore, configured 1 vCPU, 1 GB RAM, a single NIC on the YT-Intran-VLAN network, and a new 20 GB thin-provisioned disk — then attached the CentOS 9 installation ISO from the datastore so the VM could boot directly into the OS installer.
