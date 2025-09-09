1) ：Check if CPU supports and enable virtualization (Intel VT-x / AMD-V)
Windows
Check support and status

Press Win + X → Task Manager → Performance → CPU, look for Virtualization: Enabled/Disabled.

Open terminal (PowerShell or CMD):

Run systeminfo → At the end, check the Hyper-V Requirements section:

Virtualization Enabled In Firmware

VM Monitor Mode Extensions

Optional: PowerShell command: Get-ComputerInfo | Select-Object HyperV*.

Enable in BIOS/UEFI

Reboot and enter BIOS/UEFI by pressing Del / F2 / F10 / Esc (varies by vendor).

Navigate to Advanced → CPU Configuration:

Intel: enable Intel Virtualization Technology (VT-x).

AMD: enable SVM Mode / AMD-V.

Save and exit. Reboot and check again.

Linux
Check support and status

lscpu | grep -i virtualization (look for VT-x or AMD-V).

egrep -wo 'vmx|svm' /proc/cpuinfo | sort | uniq -c → vmx (Intel) or svm (AMD) means supported.

With KVM tools: kvm-ok (Ubuntu: install cpu-checker).

Enable in BIOS/UEFI

Same as Windows: enable Intel VT-x or AMD SVM, then verify again with lscpu.

macOS
Intel Macs: VT-x is usually enabled by default.

Apple Silicon (M1/M2/M3): No VT-x/AMD-V, instead use Apple Virtualization Framework (Parallels Desktop, UTM, Docker Desktop).

2) ：Why is cloud computing successful? (3 Pros, 3 Cons)
Fundamentals: Elastic scalability, pay-as-you-go model, global infrastructure, and managed services reduce entry barriers.

Pros

Elasticity and scalability: auto scale resources with demand.

Cost efficiency: pay per use, no large upfront investment.

High availability & global reach: multiple regions, reduced latency.

Cons

Vendor lock-in: migration between providers is difficult.

Compliance & data sovereignty: cross-border regulations.

Unpredictable costs: elastic resources may grow uncontrollably.

3) ：Primary function of a hypervisor
To abstract and allocate hardware resources (CPU, memory, I/O) to multiple VMs, ensuring isolation, and to provide VM lifecycle management (create, start, pause, migrate, snapshot).

4) ：What is a Virtual Machine (VM)?
A software-simulated isolated computer environment, created by a hypervisor, that allows running a guest operating system and applications.

5) ：Benefits of Virtual Machines
Isolation: workloads separated securely.

Resource consolidation: multiple VMs on one host improve utilization.

Portability: VM files can be moved across hosts.

Snapshots/Cloning: quick rollback or duplication.

Multi-OS support: run different OS side by side.

6) ：Five common use cases for VMs
Development & testing environments.

Running legacy applications.

Security sandbox / penetration testing.

Training & educational labs.

Server consolidation & disaster recovery.

7) ：In virtualization, what is the Guest Operating System?
Answer: b) The operating system installed on a virtual machine.

8) ：What does VM isolation mean?
Answer: c) Virtual machines run independently and are isolated from each other and the host system.

9) ：What is the benefit of VM portability?
Answer: c) It allows VMs to be moved between different physical machines with compatible hypervisors.

10) ：Purpose of cloning a VM
To quickly create an identical copy of an existing VM (including OS, applications, and configurations), useful for scaling, testing, backup, or training.

Types: Full Clone and Linked Clone.
