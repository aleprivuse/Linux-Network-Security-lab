# VM Setup

## VM Specifications

This time I'm going to run everything on the terminal without installing the desktop version, to try to simulate a real-world environment and make myself comfortable working only with the terminal.

The specifications of my VM are the following:

| Spec | Value |
|------|-------|
| CPU Cores | 1 |
| RAM | 5 GB |
| Hard Disk Space | 50 GB |

---

## Keyboard Configuration

My VM is using the wrong keyboard layout, so I'm going to fix it with this command:

```bash
sudo dpkg-reconfigure keyboard-configuration
```

Then go through the interface and select your keyboard layout.

After that, make sure to run `sudo reboot` to apply the new keyboard.

---

## VM Hardening

Here are the steps to secure your VM.

### Step 1 — Update everything

```bash
sudo apt update && sudo apt upgrade -y
```

This can also be automated with a script, but should at minimum be run manually every time.

### Step 2 — Configure the firewall
 Make sure to allow SSH (port 22) **before** enabling the firewall, or you might get locked out of your own machine.

```bash
sudo ufw allow 22
sudo ufw enable
```

---

## VM Connection with another VM

By default both VMs were in separate network "bubbles" (NAT mode) and ended up with the same IP address, so they couldn't see each other.

To fix this, I went to Settings → Network and changed the adapter from **NAT** to **Bridged Adapter** on both VMs. This puts them on the same network with different IPs, so they can communicate.

---

## Problems

### Problem — Corrupted ISO
I installed the VM with a corrupted Ubuntu Linux file.

**Solution:** Deleted the old VM and created a new one with a freshly downloaded Ubuntu file.

---

### Problem — Cannot run update/upgrade
The VM had the wrong system time, which caused `apt update` to fail with "Release file is not valid yet" errors.

**Solution:** Set the time manually with:
```bash
sudo date -s "YYYY-MM-DD HH:MM:SS"
```
Then verify with:
```bash
date
```

---

### Problem — Both VMs had the same IP
Both VMs were on NAT mode and got the same IP (10.0.2.15), so they couldn't communicate.

**Solution:** Changed both VMs' network adapter from NAT to Bridged Adapter — now they get different IPs on the same network and can ping each other.

