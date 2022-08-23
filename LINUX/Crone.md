
 **crontab -u username -l** - show all cron jobs for user
**crontab -l** - show cron job for logged user

**grep CRON /var/log/syslog** - show cron job 

(/var/spool/cron/crontabs/)
crontab -e  - edit job
crontab -e -u username

/var/log/cron

less /etc/crontab
nano /etc/crontab

```bash
ls -la /etc/cron.hourly
ls -la /etc/cron.daily
```

https://crontab.guru/


https://imagazine.pl/2013/03/07/jak-korzystac-z-crona-monitorowanie-zewnetrznego-ip/
https://phoenixnap.com/kb/how-to-list-display-view-all-cron-jobs-linux