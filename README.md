# virtualbox-network-playbook
VM management &amp; network recovery playbook for Kali / Metasploit labs
# Pentest Lab Ops Playbook — Kali VM Management & Network Recovery

A one-page-style operational guide for managing Kali Linux labs in VirtualBox
without breaking networking — plus rapid recovery steps when things go wrong.

This repository focuses on **prevention first**, not reinstalling VMs.

---

## 🎯 What This Covers

- Snapshot strategy before attacks
- Safe VirtualBox networking layouts
- Host VPN / proxy avoidance
- Post-lab cleanup routine
- NAT troubleshooting
- DHCP failures on host systems
- Firewall & routing resets
- Verification checklist
- Printable poster reference

---

## 🧪 Typical Lab Failures

- Kali shows connected but no internet
- NAT gateway unreachable
- DNS failures
- Host machine offline
- DHCP server not responding
- Broken routes after pivoting

---

## 🟢 Prevention Rules (Before Every Lab)

1️⃣ Take a snapshot  
2️⃣ Use NAT only unless required  
3️⃣ Disable host VPN / proxies  
4️⃣ Document routing changes  
5️⃣ Avoid saving broken VM states  

---

## ⚡ Kali 60-Second Reset Routine

```bash
sudo systemctl restart NetworkManager
sudo ip route flush table main
sudo dhclient eth0

sudo iptables -F
sudo iptables -t nat -F
sudo iptables -X
sudo nft flush ruleset

unset http_proxy https_proxy HTTP_PROXY HTTPS_PROXY
