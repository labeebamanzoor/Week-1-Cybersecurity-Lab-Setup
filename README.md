# Week 1 – Cybersecurity & Ethical Hacking Lab Setup

This repository documents the Week 1 practical task of preparing a Kali Linux virtual lab for cybersecurity and ethical hacking practice using **Oracle VirtualBox**.

## Objective

Set up and run Kali Linux in a virtual machine, configure its network connection, verify connectivity, and enable access to a shared folder.

## Lab environment

| Component | Configuration |
|---|---|
| Host operating system | Windows |
| Virtualization platform | Oracle VirtualBox |
| Guest operating system | Kali Linux |
| VM name | `kali-linux-2026.3-virtualbox-amd64` |
| Base memory | 2048 MB (2 GB) |
| Virtual processors | 2 |
| Network attachment | NAT Network (`NatNetwork`) |
| Kali IPv4 address shown in terminal | `10.0.0.2/24` |
| Shared folder mount point | `/downloads` |

The screenshots show the VM configured with 2 GB RAM and 2 virtual processors. The NAT Network name shown in VirtualBox is `NatNetwork`.

## Tasks completed

1. Installed and used Oracle VirtualBox to run Kali Linux.
2. Started the Kali Linux virtual machine successfully.
3. Configured the VM network adapter to use a VirtualBox NAT Network.
4. Configured the Kali wired connection and DNS settings.
5. Verified the Kali interface address with `ip -4 addr show eth0`.
6. Tested network connectivity and DNS resolution using `ping -c 4 google.com`.
7. Configured a VirtualBox shared folder and verified that it was mounted at `/downloads` using `findmnt -t vboxsf`.

## Network configuration

The terminal screenshot shows the Kali interface using `10.0.0.2/24`. DNS was configured with `8.8.8.8` and `1.1.1.1`. Connectivity was subsequently verified by successful ping replies from `google.com`.

See [`docs/network-configuration.md`](docs/network-configuration.md) for the commands used and verification notes.

## Shared folder

The shared folder was mounted inside Kali at:

```text
/downloads
```

The terminal output showed a VirtualBox shared-folder filesystem (`vboxsf`) with the source named `Downloads`.

See [`docs/shared-folder.md`](docs/shared-folder.md) for the setup and verification steps.

## Screenshots

- `screenshots/network-connectivity.jpeg` – Network configuration and successful ping test.
- `screenshots/virtualbox-manager.jpeg` – Kali VM running in VirtualBox Manager.
- `screenshots/kali-desktop.jpeg` – Kali Linux desktop.

## Snapshot recommendation

After confirming that Kali boots and the network and shared folder work as expected, take a baseline snapshot:

1. Return to VirtualBox Manager.
2. Select the Kali VM.
3. Open the **Snapshots** view.
4. Click **Take**.
5. Name the snapshot `Week 1 - Initial Kali Setup`.
6. Add a description of the completed setup and confirm.

A snapshot is a restore point for the virtual machine, not a substitute for backing up important files.

## Key learning outcomes

- Setting up and managing a Linux virtual machine.
- Understanding VirtualBox NAT Network mode.
- Basic IPv4 and DNS configuration.
- Testing connectivity with ping.
- Sharing files between the Windows host and Kali guest.

## Responsible use

Use Kali Linux and cybersecurity tools only on systems and networks you own or have explicit permission to test. This repository documents the lab setup and basic connectivity checks only.

---
*Week 1 – Project Module 1 | Cybersecurity & Ethical Hacking Lab Setup*
