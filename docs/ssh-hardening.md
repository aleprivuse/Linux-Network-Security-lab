 # SSH hardening 

Ps: Finish the folder VM-setup and ssh-pentest before going into this 

## Hardening


### SSH Keys


### SSH disable Root login 


## Problems
### problems 

my ~ doesnt work so im going to type long command = ´pwd´ to check where we are then in my case is `ls /home/you usernama/.ssh`





## Notes for myself 

**ssh keygen**
- login Main Vm to sub whit ssh
- create a ssh key whit this `ssh-keygen` (not gonna use passphrase but if more secure do it passphrase = password for private key)
- the find your you ssh keys whit this `ls ~/.ssh`
- then do the same to both of the VMS
- then copy your ssh key to the sub VM whi this `ssh-copy-id username@SUB_IP`
- then try to login you should be able to not use password
---
**disabilitate root login and passowrd**

- first use this `sudo nano /etc/ssh/sshd_config`
- then write inside `PermitRootLogin no`
- then use this command `sudo sshd -t`(search what it does)
- then try to login whit my Main Vm
  Root login = Disable the root login on the machine to ist harder to to brutto force it if the root is active its just `ssh root@server Ip`

  ---
  
- For the disabilitation of Passowrd its in the same place and command is `PasswordAuthentication no`
- and then run `sudo sshd -t`
  PasswordAuthentication no = its let you disisabilitate so that you can login whit an password so now the attacker cannot brutto force the way in
  `sudo sshd -t` = its checks for erros in the ssh configuration
  - now if you want to see if evering thing is valid you can try to login but you need to use special command this `ssh -o PubkeyAuthentication=no username@ip server` so it test it whitout using the keys  
