`cal Jun 2022` - show calendar

`ls /bin` - show linux command
`ls $HOME | wc -l` - quantity of files in home directory

`df -h` - partitions info
`du /var -sh` -  size of a directory
`tree /var --du -h` - tree with size of a directory

`top -d1` - info about processes running
`ps` - list of running processes
`ps -uax | grep [program]` - show pid of processe
`kill [option] [PID]` - kill processe
`kill -9 2101` - kill of processe with pid 2101 (-9 is the kill signal)
`killall mozilla` 


`last -1 $USER` - how long logged
`lognam` Print Your Login Name
`whoami` Print Current User Name

`id` The id command print user ID along with group membership of the user
`who` The who command lists logged-in users, long output
`users` Also list logged-in users, short output
`finger` Print information about users
`last` Determine when someone last logged in
`printenv` Print your environment


`wget url/filename.pdf` - download file from internet

`ip addr show eth0` - show info about ip

`touch newfile` - create new file

`sudo shutdown -h +10 "scheduled maintainance"` - shutdown system in ten minutes
`shutdown -r` or `reboot` - restart system

`ps -eo pid,comm,etime`
`ps -eo pid,comm,etime | grep "process_name"`

`cat /etc/passwd` list of all users
`groups <username>` check user group privileges
`id <username>` check user group privilages

-   **-r** – Reboots the system
-   **-h** – Halts the system
-   **-k** – Kidding: don’t realy shutdown the system but it broadcasts the warning message to all the users that the system is to going down.
-   **-c** – Cancel the shutdown in progress (If you fixed the time).
-   **-f** – On reboot, skip the usual filesystem check.
-   **-F** – On reboot, requere the filesystem check.



-   ls – Lists files in a directory.
-   cp – Copy file.
-   mv – Rename or move a file.
-   rm – Delete (remove) a file.
-   ln – Create Links to file


-   **cd** – The cd command is used for changing the directory.
-   **pwd** – The pwd command prints the current working directory.
-   **basename** – The basename command prints the final part of a file path.
-   **dirname** – The dirname command prints a file path without its final part.
-   **mkdir** – The mkdir command is used for creating a directory.
-   **rmdir** – The rmdir command is use for removing an empty directory.
-   **rm -r** – The rm -r command is used for removing a directory and its contents.

-   **df** – The df command is use to display available space on mounted filesystem.
-   **mount** – The mount command is use to mount the partition.
-   **unmount** – The unmount command unmounts a disk partition.
-   **fsck** – The fsck command check disk partition for error.
-   **eject** – The eject command ejects CD, DVD, or other removeable disk

-   **cat** – By running the cat command you will be able to view the file in its entirety.
-   **less** – View text file one page at a time.
-   **nl** – View file with line numbering.
-   **head** – View the first line of the text file.
-   **tail** – View the last line of the file.
-   **string** – string is used to text that’s embedded in a binary file.
-   **od** – View the data in octal

`column -tns: /etc/passwd` - good-looking password file 

**history -c** - clear history


*nohup java -jar jarname.jar &* - run app in background

**make a Java application run permanently**
1. sudo nano /etc/systemd/system/new_app.service
```
[Unit]  
Description=Name Java Application  
After=network.target  
  
[Service]  
ExecStart=/usr/bin/java -jar /path/to/new_app.jar  
WorkingDirectory=/path/to/new_app  
Restart=always  
RestartSec=30
User=username  
  
[Install]  
WantedBy=multi-user.target
```
2. sudo systemctl daemon-reload
3. sudo systemctl start new_app
4. sudo systemctl enable new_app

```
journalctl -u service-name.service -b
```
Check port number for ssh: ```
sudo netstat --tcp --numeric-ports --listening --program | grep sshd
```