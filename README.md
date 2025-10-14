How to – Install Vicidial on Alma Linux 9 with my new auto installer

That’s right, I have fixed the issues with dahdi and php7 installations on Alma Linux 9 and created the auto installer for it, complete with the dynamic portal and the CyburPhone. Its been tested and is working. So lets get to it! The code can be found here: https://github.com/carpenox/vicidial-install-scripts/tree/main
image 101361114 15620151

Alma 9 ISO – https://repo.almalinux.org/almalinux/9/isos/x86_64/AlmaLinux-9-latest-x86_64-dvd.iso
Step 1 – Download the dependencies

timedatectl set-timezone America/New_York

yum check-update
yum update -y
yum -y install epel-release
yum update -y
yum install git -y
yum install kernel* --exclude=kernel-debug* -y

#Disable SELINUX
sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config    


cd /usr/src
git clone https://github.com/carpenox/vicidial-install-scripts.git
cd vicidial-install-scripts

reboot

image 101361114 15620149
Step 2 – Run the installer

Now yes this an auto installer, but you have to hit enter a couple times as well as add the server’s IP so don’t walk away for too long.

Make sure you have (FQDN) Full Qualified Domain name

chmod +x main-installer.sh
./main-installer.sh

For other versions check here: https://github.com/carpenox/vicidial-install-scripts

Some more in-depth information about the installer can be found here:
