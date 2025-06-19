## What is a Cron Process?

The **cron** process is a **daemon** — a background process — that runs on Unix/Linux systems and is responsible for executing scheduled tasks automatically at specified times and intervals.
- It runs continuously in the background.
- It wakes up every minute to check if any tasks are due.
- If it finds a matching task in the crontab, it executes it.

You can check if cron is running using:

```bash
ps aux | grep cron
```

---

## What is a Crontab?

A **crontab** (short for "cron table") is a file that lists jobs (commands or scripts) and the times they should be run. Each user (including root) can have their own crontab file.

To view or edit your crontab:
- View: `crontab -l`
- Edit: `crontab -e`
- Remove: `crontab -r`

---

## Crontab Format

Each line in a crontab file follows this format:

```
* * * * * /path/to/command
│ │ │ │ │
│ │ │ │ └─── Day of the week (0 - 7) (Sunday=0 or 7)
│ │ │ └───── Month (1 - 12)
│ │ └─────── Day of the month (1 - 31)
│ └───────── Hour (0 - 23)
└─────────── Minute (0 - 59)
```

### Example:

```bash
30 2 * * 1 /home/user/backup.sh
```

This means: run `/home/user/backup.sh` every **Monday** at **2:30 AM**.

---

## Special Strings in Crontab

You can also use shortcuts:

|String|Meaning|
|---|---|
|`@reboot`|Run once at startup|
|`@yearly`|Run once a year (`0 0 1 1 *`)|
|`@monthly`|Run once a month (`0 0 1 * *`)|
|`@weekly`|Run once a week (`0 0 * * 0`)|
|`@daily`|Run once a day (`0 0 * * *`)|
|`@hourly`|Run once an hour (`0 * * * *`)|

Example:

```bash
@daily /usr/local/bin/daily_report.sh
```

---

## Writing a Crontab Entry

When you use `crontab -e`, it opens the file in a text editor (like `vi` or `nano`). You just write the schedule and the command.

Example:

```bash
0 18 * * * /usr/bin/python3 /home/user/send_report.py >> /home/user/log.txt 2>&1
```

This runs every day at 6:00 PM and logs both stdout and stderr to `log.txt`.

---

## Common Tips

- Always use **absolute paths** in cron commands (cron doesn’t load user profiles).
- Redirect output to a file for debugging (`>> log.txt 2>&1`).
- You can specify ranges and lists:

```bash
0 9-17 * * 1-5 command   # Every hour from 9 to 5, Monday to Friday
*/15 * * * * command     # Every 15 minutes
```

---

## System-wide Crontabs

- `/etc/crontab` – system-wide crontab.
- `/etc/cron.d/` – put custom job files here.
- `/etc/cron.daily/`, `/etc/cron.hourly/`, etc. – run jobs at specific intervals.

System crontabs include a **user field**:

```
* * * * * username /path/to/command
```

---

## References

https://tryhackme.com/room/linuxfundamentalspart3