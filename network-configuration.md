# Network Configuration

This document records the network configuration shown in the Week 1 Kali Linux lab screenshots.

## Observed configuration

| Setting | Value |
|---|---|
| Network adapter in VirtualBox | NAT Network |
| NAT Network name | `NatNetwork` |
| Kali interface | `eth0` |
| IPv4 address | `10.0.0.2/24` |
| DNS servers configured | `8.8.8.8`, `1.1.1.1` |

The screenshots establish the Kali interface address and DNS settings. The exact NAT Network gateway and DHCP pool are not documented in the screenshots, so check the NAT Network settings in VirtualBox rather than assuming a gateway value.

## Find the active connection name

```bash
nmcli connection show
```

In this setup, the wired profile was named:

```text
Wired connection 1
```

## Configure DNS

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dns "8.8.8.8 1.1.1.1"
sudo nmcli connection modify "Wired connection 1" ipv4.ignore-auto-dns yes
```

Apply the connection:

```bash
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

The screenshot shows that the connection was successfully activated after restarting NetworkManager and reconnecting the `eth0` device.

## Verify IP address and connectivity

```bash
ip -4 addr show eth0
ping -c 4 google.com
```

The interface output showed:

```text
inet 10.0.0.2/24
```

The subsequent ping test received four replies with 0% packet loss, demonstrating successful name resolution and connectivity at the time of testing.

## Troubleshooting note

An earlier ping attempt returned a temporary name-resolution error. DNS was then configured and the connection reactivated; the later ping test succeeded. If the issue returns, check the VirtualBox NAT Network attachment, DNS settings, and connection status.
