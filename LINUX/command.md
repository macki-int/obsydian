adduser username
deluser username
deluser --remove-home username

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