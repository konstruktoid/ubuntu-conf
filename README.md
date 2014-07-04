ubuntu-conf  
===========
  
ubuntu_config.sh is a script to harden a Ubuntu server.  
  
Configuration options are as follows:  
FW_ADMIN="192.168.2.100" *The IP address that will be able to connect with SSH.*  
SSH_GRPS="sudo" *Which group the users have to be member of in order to acess via SSH.*  
FW_CONF="https://raw.githubusercontent.com/konstruktoid/ubuntu-conf/master/net/firewall.conf" *Skeleton firewall configuration*  
FW_POLICY="https://raw.githubusercontent.com/konstruktoid/ubuntu-conf/master/net/firewall" *Skeleton firewall configuration*  
SYSCTL_CONF="https://raw.githubusercontent.com/konstruktoid/ubuntu-conf/master/misc/sysctl.conf " *Stricter sysctl settings*  
VERBOSE="N" If you want all the details or not   
CHANGEME="" Add something just to verify that you actually glanced the code  
  
It's meant to be run from the console, and directly after a server has been installed.  
It applies a strict firewall that only allows specified IP addresses to connect to SSH.  
It then adds /tmp and /var/tmp mount options, modifies /etc/login.defs and downloads a new sysctl.conf.  
After the sysctl.conf settings has been applied it changes limits.conf, the default shell and root access.conf.  
ubuntu_config.sh then installs libpam-tmpdir, libpam-cracklib, apparmor-profiles, ntp, openssh-server and open-vm-tools.  
SSHd is then configured to allow members of $SSH_GRPS and sets LoginGraceTime to 20.  
/etc/pam.d/common-password includes minlen=14 and remember=5.  
Only root is allowed to use cron and at.  
Last but not least, suid bits are removed.  
  
Tested on 14.04 LTS.   
  
Recommended reading:  
Guide to the Secure Configuration of Red Hat Enterprise Linux 5  
CIS Ubuntu 12.04 LTS Server Benchmark v1.0.0   
https://wiki.ubuntu.com/Security/Features  
https://help.ubuntu.com/community/StricterDefaults  


