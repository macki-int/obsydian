 list of runnin processes**sudo crontab -u username -l** - all cron jobs user


grep CRON /var/log/syslog - show cron job 

/var/log/cron

less /etc/crontab
nano /etc/crontab

```bash
ls -la /etc/cron.hourly
ls -la /etc/cron.daily
```

crontab -l - show cron job
(/var/spool/cron/crontabs/)
crontab -e  - edit job
crontab -e -u username

https://imagazine.pl/2013/03/07/jak-korzystac-z-crona-monitorowanie-zewnetrznego-ip/

https://phoenixnap.com/kb/how-to-list-display-view-all-cron-jobs-linux