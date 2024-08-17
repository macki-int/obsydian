`sudo apt install hplip`
`sudo usermod -a -G lpadmin <username>`
`sudo nano /etc/cups/cupsd.conf`
change `Listen localhost:631` on  `Listen Port 631`
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
in browser (CUPS managment) `http://<IP>:631`
and move *Adminstration*  -> *Add printer* -> *Maintenance* -> *Print Test Page*


https://raspberrytips.com/install-printer-raspberry-pi/
https://forums.raspberrypi.com/viewtopic.php?t=325281
https://developers.hp.com/hp-linux-imaging-and-printing/plugins