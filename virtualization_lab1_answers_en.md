# Virtualization – Lab 1 Answers and Steps
*Last updated: 2025-09-09 04:14*

> Tip: This file can be directly placed in your GitHub repository as `README.md`.

---

## 1) Check if CPU supports and enable virtualization (Intel VT-x / AMD-V)

### Windows
**Check support and status**
1. Press `Win + X` → **Task Manager** → **Performance** → **CPU**, look for **Virtualization: Enabled/Disabled**.
2. Open terminal (PowerShell or CMD):  
   - Run `systeminfo` → At the end, check the **Hyper-V Requirements** section:  
     - *Virtualization Enabled In Firmware*  
     - *VM Monitor Mode Extensions*  
3. Optional: PowerShell command: `Get-ComputerInfo | Select-Object HyperV*`.

**Enable in BIOS/UEFI**
1. Reboot and enter BIOS/UEFI by pressing **Del / F2 / F10 / Esc** (varies by vendor).  
2. Navigate to **Advanced → CPU Configuration**:  
   - Intel: enable **Intel Virtualization Technology (VT-x)**.  
   - AMD: enable **SVM Mode / AMD-V**.  
3. Save and exit. Reboot and check again.

### Linux
**Check support and status**
1. `lscpu | grep -i virtualization` (look for VT-x or AMD-V).  
2. `egrep -wo 'vmx|svm' /proc/cpuinfo | sort | uniq -c` → **vmx** (Intel) or **svm** (AMD) means supported.  
3. With KVM tools: `kvm-ok` (Ubuntu: install `cpu-checker`).  

**Enable in BIOS/UEFI**
- Same as Windows: enable **Intel VT-x** or **AMD SVM**, then verify again with `lscpu`.

### macOS
- Intel Macs: VT-x is usually enabled by default.  
- Apple Silicon (M1/M2/M3): No VT-x/AMD-V, instead use **Apple Virtualization Framework** (Parallels Desktop, UTM, Docker Desktop).

---

## 2) Why is cloud computing successful? (3 Pros, 3 Cons)
**Fundamentals**: Elastic scalability, pay-as-you-go model, global infrastructure, and managed services reduce entry barriers.

**Pros**
1. **Elasticity and scalability**: auto scale resources with demand.  
2. **Cost efficiency**: pay per use, no large upfront investment.  
3. **High availability & global reach**: multiple regions, reduced latency.  

**Cons**
1. **Vendor lock-in**: migration between providers is difficult.  
2. **Compliance & data sovereignty**: cross-border regulations.  
3. **Unpredictable costs**: elastic resources may grow uncontrollably.  

---

## 3) Primary function of a hypervisor
- To **abstract and allocate hardware resources** (CPU, memory, I/O) to multiple VMs, ensuring isolation, and to provide VM lifecycle management (create, start, pause, migrate, snapshot).

---

## 4) What is a Virtual Machine (VM)?
- A **software-simulated isolated computer environment**, created by a hypervisor, that allows running a **guest operating system** and applications.

---

## 5) Benefits of Virtual Machines
1. **Isolation**: workloads separated securely.  
2. **Resource consolidation**: multiple VMs on one host improve utilization.  
3. **Portability**: VM files can be moved across hosts.  
4. **Snapshots/Cloning**: quick rollback or duplication.  
5. **Multi-OS support**: run different OS side by side.  

---

## 6) Five common use cases for VMs
1. Development & testing environments.  
2. Running legacy applications.  
3. Security sandbox / penetration testing.  
4. Training & educational labs.  
5. Server consolidation & disaster recovery.  

---

## 7) In virtualization, what is the Guest Operating System?
**Answer: b) The operating system installed on a virtual machine.**

---

## 8) What does VM isolation mean?
**Answer: c) Virtual machines run independently and are isolated from each other and the host system.**

---

## 9) What is the benefit of VM portability?
**Answer: c) It allows VMs to be moved between different physical machines with compatible hypervisors.**

---

## 10) Purpose of cloning a VM
- To **quickly create an identical copy** of an existing VM (including OS, applications, and configurations), useful for **scaling, testing, backup, or training**.  
- Types: **Full Clone** and **Linked Clone**.

---

## GitHub Repository Guide

1. **Create repository**
   - Go to GitHub → **New repository** → name it `virtualization-labs`, optionally select `Add a README`.

2. **Local setup and push**
```bash
# Create project folder
mkdir virtualization-labs && cd virtualization-labs

# Move this file as README
mv virtualization_lab1_answers_en.md README.md

# Initialize Git and commit
git init
git add .
git commit -m "Add Lab 1 answers and steps"

# Connect to remote
git branch -M main
git remote add origin https://github.com/<YOUR-USER>/virtualization-labs.git
git push -u origin main
```

3. **Share**
   - Share the repository link or add `robustness@gmail.com` as a collaborator.

---

## Optional Validation
- Provide screenshots:  
  - Windows Task Manager → CPU → Virtualization: Enabled.  
  - Linux `lscpu` or `kvm-ok` output.  
  - A VM successfully created and launched in Hyper-V, VirtualBox, or VMware.

> Completing the above covers all questions and steps for Lab 1.
