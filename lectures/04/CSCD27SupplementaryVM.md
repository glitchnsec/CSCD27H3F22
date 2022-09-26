---
layout: default
permalink: /misc/SupplementaryVM
---

## Notes ##
- You may not need this if you having a working docker installation on your physical machine or another virtual machine
- This VM is provided as-is with no warranty. It is still preferrable to do lab work in the CS Labs in-person
- If you use Hyper-V i.e any of Windows Sandbox, WSL, Hyper-V Manager etc. You'll need to disable Hyper-V to use any other virtualization technology. Porting this VM to Hyper-V is beyond the scope of this provision however, it is fairly trivial to create a similar Hyper-V VM given the configuration's below.

## Requirements ##
- Basic understanding of virtualization
- Virtualization Platform (any of):
    - [VMWare Workstation](https://customerconnect.vmware.com/en/downloads/info/slug/desktop_end_user_computing/vmware_workstation_player/16_0)
    - [VMware Fusion](https://customerconnect.vmware.com/evalcenter?p=fusion-player-personal)

- Provided resources
    - [CSCD27-supplementary-vm.ova](https://utoronto-my.sharepoint.com/:u:/g/personal/kc_udonsi_mail_utoronto_ca/ETgmPgVr_-tJq9lipPYF7pUBZnrknOQH_-vtmG2K9m6pPg?e=hYNhFP)
    - Prof. Thierry's [Introduction to Docker](https://glitchnsec.github.io/CSCD27H3F22/doc/docker/)

## Summary ##
- Refer to the [Introduction to Docker](https://glitchnsec.github.io/CSCD27H3F22/doc/docker/) documentation to familiarize yourself with docker in the provided VM.

- The virtual machine provided has been configured with the following specifications:

    | Configuration | Value |
    |:----|:----|
    | Ram | 4GB |
    | Disk | 20GB |
    | vProc | 4 |
    | Docker | Installed - |
    | Python | Installed - 3.10.8|
    | Wireshark | Installed - |
    | Password | Passw0rd! **(WARNING: Weak password)**|
    | Virtualization (intel vt-x/amd-v) | Enabled if supported by host |
    | SSH | Enabled |
    | IP | dynamic |
    | Network | NAT (will use your host's network)|
