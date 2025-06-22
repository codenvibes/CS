In Linux, logs are essential for monitoring system performance, diagnosing issues, and auditing events. Logs are typically stored as plain text files and managed by the `syslog` system or more modern services like `journald` (part of `systemd`).

## Common Log Files in Linux (`/var/log/`)

Here's a breakdown of the most important log files:

| Log File                                 | Description                                                                                    |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `/var/log/syslog` or `/var/log/messages` | General system activity logs. Debian-based systems use `syslog`; Red Hat-based use `messages`. |
| `/var/log/auth.log`                      | Authentication logs (logins, sudo attempts, etc.)                                              |
| `/var/log/kern.log`                      | Kernel logs (useful for debugging hardware/kernel issues)                                      |
| `/var/log/dmesg`                         | Boot and kernel ring buffer messages                                                           |
| `/var/log/boot.log`                      | Boot-related messages                                                                          |
| `/var/log/faillog`                       | Failed login attempts                                                                          |
| `/var/log/lastlog`                       | Last login info for all users                                                                  |
| `/var/log/btmp`                          | Binary log of failed login attempts (use `lastb` to read)                                      |
| `/var/log/wtmp`                          | Binary log of all login/logout events (use `last` to read)                                     |
| `/var/log/apt/`                          | Logs from the APT package manager (Debian/Ubuntu)                                              |
| `/var/log/yum.log`                       | Logs from the YUM package manager (Red Hat/CentOS)                                             |
| `/var/log/httpd/` or `/var/log/apache2/` | Web server logs (Apache)                                                                       |
| `/var/log/nginx/`                        | Web server logs (Nginx)                                                                        |
| `/var/log/mysql/` or `/var/log/mariadb/` | Database logs                                                                                  |

---

## Viewing Logs

You can view logs using standard text tools:

```bash
cat /var/log/syslog
less /var/log/auth.log
tail -f /var/log/syslog  # Follow live logs
```

Or use:

```bash
journalctl              # View systemd logs
journalctl -xe          # Show most recent errors
journalctl -u nginx     # Logs for a specific service
```

---

## Log Rotation

Logs can grow large, so Linux uses **logrotate** to manage them:

- Config: `/etc/logrotate.conf` and `/etc/logrotate.d/`
- Rotation includes compressing old logs, deleting old ones, etc.

---

## Useful Commands

```bash
dmesg                # View boot and kernel messages
last                 # Show login history
lastb                # Show failed login attempts
who                  # Who is logged in
uptime               # System load and uptime
```

---

## Linux Fundamentals Part 3


---

## References

https://tryhackme.com/room/linuxfundamentalspart3