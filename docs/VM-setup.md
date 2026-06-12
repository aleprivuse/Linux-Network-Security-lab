# VM setup 

 ## VM Specification

This time im goign to run everything i do on the terminal whitout installing the deskop version to try to simulate a real world enviroment and making myself confortable working only whit the terminal. 
The Specification i got on my VM are the following :

1. CPU Core = 1
2. RAM = 5 gb
3. Hard Disk Space = 50gb

## Keyboard Configuration

My VM is using another Keyboard so im going to fix it whit this command

```bash
sudo dpkg-reconfigure keyboard-configuration
```

then you are gonna go to the interface and select your keyboard.

After that make sure to do `sudo reboot` to use the new keyboard
## VM Hardening

Here are gonna be the step to how secure your VM 
### Step 1

First make sure you make all of the update for you VM you can use i script or just putting this command manually every time `sudo apt update && sudo apt upgrade -y `

## VM Connection whit another VM

## Problems

### Problems

I installed the VM whit a corrupted Ubuntu Linux file 

### Solution:

Deleted the old VM and created a new one whit a new installed Ubuntu file

### Problems = Cannot do update and upgrade

The vm has still the old time so i needed find a way to fix it.

### Solution 

I had to set the time manually whit this command `sudo date -s "(put you date)"`

Then check angain whit `date` if you changed it 
