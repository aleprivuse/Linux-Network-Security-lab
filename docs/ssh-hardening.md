# SSH Hardening

> **Prerequisite:** Finish the VM Setup and SSH Pentest labs before continuing.

## SSH Keys

SSH keys allow you to log in without using a password. Instead of typing a password every time, you use a public/private key pair.

### Generate a Key Pair

```bash
ssh-keygen
```

> I am not using a passphrase for this lab, but for better security you should use one. A passphrase acts like a password for your private key.

Check your keys:

```bash
ls ~/.ssh
```

Copy the public key to the Sub VM:

```bash
ssh-copy-id username@SUB_IP
```

Try logging in again. You should now be able to log in without entering a password.

---

## Disable Root Login

Open the SSH configuration:

```bash
sudo nano /etc/ssh/sshd_config
```

Add or modify:

```text
PermitRootLogin no
```

Check for errors:

```bash
sudo sshd -t
```

### Why?

Disabling root login prevents attackers from directly targeting the root account.

Without this setting, an attacker could try:

```bash
ssh root@SERVER_IP
```

---

## Disable Password Authentication

In the same file:

```bash
sudo nano /etc/ssh/sshd_config
```

Add or modify:

```text
PasswordAuthentication no
```

Validate the configuration:

```bash
sudo sshd -t
```

### Why?

This disables password-based logins and forces users to authenticate with SSH keys.

To test it:

```bash
ssh -o PubkeyAuthentication=no username@SERVER_IP
```

Expected result:

```text
Permission denied (publickey)
```

---

## Result

* SSH key authentication enabled
* Root login disabled
* Password authentication disabled
* Brute-force attacks significantly harder

---

## What I Learned

* How SSH key authentication works
* How to generate SSH keys
* How to copy SSH keys to another server
* How to disable root login
* How to disable password authentication
* How to validate SSH configuration files with `sshd -t`
* Why SSH keys are more secure than passwords

---

## Problems

### Problem

My `~` shortcut was not working.

### Solution

Check where you are:

```bash
pwd
```

Then manually locate the SSH directory:

```bash
ls /home/your_username/.ssh
```
