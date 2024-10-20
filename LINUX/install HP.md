`sudo apt install hplip`
`sudo usermod -a -G lpadmin <username>`  *(sudo usermod -aG lpadmin username)*
`sudo nano /etc/cups/cupsd.conf`
change `Listen localhost:631` on  `Port 631`
add `Allow @local`
```
<Location />
  Order allow,deny
  Allow @local
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow @local
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow @local
</Location>
```
`sudo service cups restart
`
`hp-plugin`
turn on printer
better driver (additional install after hplip):  ```apt install printer-driver-foo2zjs```

in browser (CUPS managment) `http://<IP>:631`
**Add printer** (check if system see device *lsusb*): *Adminstration*  -> *Add printer*

![[Pasted image 20241020192305.png]]

Print test page: *Adminstration*  -> *Add printer* -> *Maintenance* -> *Print Test Page*

https://raspberrytips.com/install-printer-raspberry-pi/
https://forums.raspberrypi.com/viewtopic.php?t=325281
https://developers.hp.com/hp-linux-imaging-and-printing/plugins
https://unix.stackexchange.com/questions/179549/what-connection-should-i-enter-for-usb-printer-hplip


*random notes:*
apt show hplip
hp-plugin -p <plugin_name.run> (needed .run.asc too)
hp-setup -i

hp-check -t
apt purge hplip-data

journalctl -u cups -e