---
layout: default
permalink: /doc/docker/vm/
---

## Notes ##
- You may not need this if you having a working docker installation on your physical machine or another virtual machine
- This VM is provided as-is with no warranty. It is still preferrable to do lab work in the CS Labs in-person
- If you use Hyper-V i.e any of Windows Sandbox, WSL, Hyper-V Manager etc or have intel vt-x/amd-v unavailable for some reason. ~~You'll need to disable Hyper-V to use any other virtualization technology. Porting this VM to Hyper-V is beyond the scope of this provision however, it is fairly trivial to create a similar Hyper-V VM given the configuration's below.~~ Use the VM tagged "noVirt".

## Requirements ##
- Basic understanding of virtualization
- Virtualization Platform (any of):
    - [VMware Workstation](https://customerconnect.vmware.com/en/downloads/info/slug/desktop_end_user_computing/vmware_workstation_player/16_0)
    - [VMware Fusion](https://customerconnect.vmware.com/evalcenter?p=fusion-player-personal)

- Provided resources

    - [CSCD27-supplementary-vm.ova \| 6.4GB \|](https://utoronto-my.sharepoint.com/:u:/g/personal/kc_udonsi_mail_utoronto_ca/ETgmPgVr_-tJq9lipPYF7pUBZnrknOQH_-vtmG2K9m6pPg?e=hYNhFP) | sha256: `FC40554BCD40585A7214BC64B7AB04D75CCF352C6F977CB2DDD00122ABB1B6E7`
    - [CSCD27-supplementary-vm-noVirt.ova \| 6.5GB \|](https://utoronto-my.sharepoint.com/:u:/g/personal/kc_udonsi_mail_utoronto_ca/EeWul2UkjjxFmycAob1rlb0BjEsRhope2pwNLiVSoAsiFQ?e=TGf1Gi) | sha256: `A9AE590AC68A35522567CA22484C2F9C2B05A23670B1B79E008D6E29746B162E`
    - Prof. Thierry's [Introduction to Docker](https://glitchnsec.github.io/CSCD27H3F22/doc/docker/)

## Summary ##
- Refer to the [Introduction to Docker](https://glitchnsec.github.io/CSCD27H3F22/doc/docker/) documentation to familiarize yourself with docker in the provided VM.

- The virtual machine provided has been configured with the following specifications:

    | Configuration | Value |
    |:----|:----|
    | OS | Ubuntu 22.04.1 LTS|
    | Ram | 4GB |
    | Disk | up to 20GB, Dynamic |
    | vProc | 4 |
    | Docker | Installed - 20.10.18, build b40c2f6|
    | Python | Installed - 3.10.6|
    | Wireshark | Installed - 3.6.2|
    | Password | Passw0rd! **(WARNING: Weak password)**|
    | Virtualization (intel vt-x/amd-v) | Enabled in CSCD27-supplementary-vm.ova<br>Disabled in CSCD27-supplementary-vm-noVirt.ova |
    | SSH | Enabled |
    | IP | Dynamic |
    | Network | NAT (will use your host's network)|
