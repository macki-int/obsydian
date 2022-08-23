adduser username
deluser username
deluser --remove-home username
usermod [option] username - modifying user's account (-L / -U lock / unlock)

**passwd username**  - change user password

**uname -a** - print info about system
**sudo  lshw** - print hardware configuration
**sudo  lshw -short** - print shorter of hardware configuration
**sudo lshw -html > lshw.html** - to html
**lscpu** - print info about CPU
**lsblk** - print info about storages
**lsusb** - print info about usb
**sudo hdparm **/dev/sda1**** print info about sata device
**fdisk** - print info about system partitions
**sudo dmidecode -t memory** - info about memory
**sudo dmidecode -t system** - info about system
**sudo dmidecode -t bios** - info about bios
**sudo dmidecode -t processor** - info about CPU

cat

free -g
free -m
vmstat
top 
cat /proc/meminfo
htop
 ip -adrr - aho net address

sudo pkill -u username - logout user


neofetch - show system info
df -h  system disk info

  
**find -name "file_name"** -maxdepth 1 - finding file in the folder
**find -name "*part_of_file_name*"** -maxdepth 1 - finding file in the folder
**find -iname "file_name"** -maxdepth 1 - finding file in the folder with Upper and Lower letters

apt install sudo
**usermod -aG sudo username** - add user to sudo group
**sudo su -** - back to root

`ss -nlt | grep LISTEN` - show all listen ports

`journalctl -u service-name` - status service
`journalctl -u service-name.service -b` status messages for current boot
`journalctl -xe`


`systemctl list-sockets --all`  - show all sockets with inactive too 

**show system log**  (https://ackcent.com/basics-linux-events-logging/)
log folder /var/log/
`systemctl list-sockets --all`  - show all sockets with inactive too 

`logger -u /run/systemd/journal/syslog`
tail -f syslog

**cat /etc/passwd** - list all users


**passwd -l username** lock user passwd
**passwd -u username** unlock user passwd

**passwd --status root**- Check if the user account is locked.

grep ^root /etc/passwd  - check for non-interactive shell

ps -xa  list of running processes

**chown -R {user:grupe} {directory}** -  recursive change of owner

**chmod 777 foldername** will give read, write, and execute permissions for everyone.
**chmod 700 foldername** will give read, write, and execute permissions for the user only.
**chmod 327 foldername** will give write and execute (3) permission for the user, w (2) for the group, and read, write, and execute for the users.

https://chmodcommand.com
