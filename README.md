# public-ip-finder
Bash Public IP finder

This script was inspired from [K0p1-Git/cloudflare-ddns-updater](https://github.com/sina-kamali/cloudflare-ddns-updater.git)

Simple bash script to find the current public IP and store it in a file

# Automation in Ubuntu
You can automate this task by 
```sh
crontab -e
```

```text
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
```

```sh
*/1 * * * * /bin/bash /PATH_TO_SCRIPT/public-ip-finder/ip-finder.sh
```
```sh
sudo systemctl restart cron
```


# Block by IP in HaProxy
```code
acl allowed_ip hdr_ip(x-forwarded-for,-1)  -f /home/public-ip-finder/server-public-ip.ips
http-request deny if !allowed_ip
```



