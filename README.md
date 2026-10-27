<div align="center">

# 🔐 Cybersecurity Lab Environment Setup

**Building an isolated virtual lab for penetration testing and ethical hacking practice**
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
</p>

---

## 📌 Project Overview

This project focuses on setting up a **virtual cybersecurity and penetration-testing laboratory** using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

---

## 🎯 Objectives

The main objectives of this project are to:

- Install and configure VirtualBox.
- Install/import Kali Linux as a virtual machine.
- Create a private **NAT Network** for the cybersecurity lab.
- Configure network connectivity for Kali Linux.
- Assign a consistent IP address to the Kali VM.
- Verify network connectivity and DNS resolution.
- Take a clean VM snapshot for recovery.
- Document the complete setup process.
- Prepare the environment for future cybersecurity projects.

---

## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security-tool experimentation

⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## ⚙️ Lab Configuration

| 🧩 Component        | ⚙️ Configuration    |
| ------------------ | ------------------  |
| 🖥️ Host OS         | Windows 10          |
| 🧠 Host RAM         | 8 GB                |
| 🧰 Hypervisor      | VirtualBox 7.2      |
| 🐉 Security OS     | Kali Linux 2026.2   |
| 🧠 Kali RAM         | 7.8 GiB (~8 GB)     |
| 🌐 Virtual Network | NAT Network (NW-Lab)|
| 📡 Network Address | 10.0.0.0/24         |
| 🐧 Kali IP Address | 10.0.0.2/24         |
| 🚪 Default Gateway | 10.0.0.1            |
| 🌍 DNS Server      | 8.8.8.8             |
| 🔮 Future VM Range | 10.0.0.3–10.0.0.99 |

---

# 🪜 Lab Setup Procedure

## Step 1. Install 7-Zip & VirtualBox

7-Zip was installed to extract virtual machine archives, and VirtualBox was installed as the primary hypervisor with hardware virtualization (VT-x) enabled in the host system BIOS.

---

## Step 2. Create the NAT Network

A dedicated NAT Network was created in VirtualBox to allow isolated internal communication between virtual machines while supporting outbound Internet access.

**Configuration:**
- **Network Name:** `NW-Lab`
- **IPv4 Prefix:** `10.0.0.0/24`
- **DHCP:** Enabled
- **IPv6:** Disabled

![NAT Network Settings](nat-network-config.png)

---

## Step 3. Import & Configure Kali Linux

The Kali Linux virtual machine was imported into VirtualBox and configured on the `NW-Lab` NAT Network. A shared folder (`sf_Downloads`) was mounted for seamless host-to-guest file transfers.

**VM Hardware & Network Parameters:**
- **RAM:** `7.8 GiB (~8 GB)`
- **Adapter 1:** Attached to `NAT Network` (`NW-Lab`)

![Kali Linux Desktop Environment](kali-desktop.png)

---

## Step 4. Network Verification & Baseline Snapshot

Network connectivity, DNS resolution (`nslookup`), and IP routing (`ping 8.8.8.8`) were verified directly within the Kali Linux terminal environment. Following successful tests, a baseline VirtualBox VM snapshot was saved for recovery purposes.

---

# 🔎 Lab Verification

| ✅ Test                         | 🧾 Command                      | 🎯 Expected Result              |
| ----------------------------- | ------------------------------- | ------------------------------- |
| 🌐 Check IP address            | `ip a`                          | Correct Kali IP displayed       |
| 📡 Test gateway                | `ping 10.0.0.1`                 | Successful replies              |
| 🌍 Test Internet connectivity | `ping 8.8.8.8`                  | Successful replies              |
| 🔎 Test DNS resolution         | `nslookup networkwalks.com`     | Domain resolves                 |
| 🧰 Verify Nmap                 | `nmap --version`                | Nmap version displayed          |
| 🔄 Verify snapshot             | Restore snapshot and run `ip a` | Baseline configuration restored |

---

# 🐞 Problems Encountered & Solutions

## Problem 1. Continuous Ping Execution in Linux Terminal

**Issue:** Running `ping google.com` kept scrolling continuously without auto-terminating.  
**Resolution:** Learned that Linux `ping` runs indefinitely by default (unlike Windows). Stopped the execution cleanly using the key combination `Ctrl + C`.

## Problem 2. VirtualBox VT-x / Virtualization Error

**Issue:** The VM failed to start due to hardware virtualization being disabled in system firmware.  
**Resolution:** Enabled Intel VT-x/AMD-V virtualization settings inside system BIOS/UEFI prior to booting the Kali VM.

---

# 💡 What I Learned

1. **NAT Network Dynamics:** Understood how a shared NAT Network enables inter-VM communication while preserving outbound WAN connectivity.
2. **Linux Network Diagnostics:** Mastered essential CLI tools (`ip a`, `ping`, `nslookup`, `nmcli`) in Kali Linux.
3. **VM Baseline Preservation:** Recognized the critical role of VM snapshots prior to conducting experimental security testing.

---

# 🔐 Security & Ethical Use

This laboratory is intended strictly for educational purposes and authorized penetration testing exercises.

---

# 🔗 Tools & Resources

- **7-Zip:** [https://7-zip.org/download.html](https://7-zip.org/download.html)
- **VirtualBox:** [https://virtualbox.org/wiki/Downloads](https://virtualbox.org/wiki/Downloads)
- **Kali Linux:** [https://kali.org/get-kali](https://kali.org/get-kali)

---

# 👤 Author

**Gaurav Ravindra Chalke**  
Cybersecurity Trainee | NetworkWalks Batch B084

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 01 | **Project:** Cybersecurity & Pentesting Lab Setup | **Repository:** GitHub
