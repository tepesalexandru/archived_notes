#linux #LPIC-1 

### What is a Cron?
Cron is a job scheduling utility present in Unix like systems.

The `cron` enables cron functionality and runs in background. It also reads the `crontab` (cron tables) for running predefined scripts.

By using a specific syntax, you can configure a cron job to schedule scripts or other commands to run automatically.

For individual users, the `cron` service checks the following file `/var/spool/cron/crontabs`.

### What are cron jobs?
Any task that you schedule through crons is called a `cron job`.

Cron jobs help us automate our routing tasks, whether they're hourly, daily, monthly, or yearly.

In order to use cron jobs, an admin needs to allow cron jobs to be added for users in the `/etc/cron.allow` file. If `cron.allow`

Users can also be denied access to cron job access by entering their usernames in the file `/etc/cron.d/cron.deny`.