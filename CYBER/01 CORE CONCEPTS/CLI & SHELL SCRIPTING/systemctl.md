
`systemctl` is a command-line tool used to **examine and control the `systemd` system and service manager** on Linux systems (like Ubuntu, CentOS, Fedora, Debian, Arch, etc.). `systemd` is the default init system on most modern Linux distributions and manages everything from services and daemons to devices and sockets.


## Common `systemctl` Commands

### 1. Starting and Stopping Services

```bash
sudo systemctl start <service-name>
sudo systemctl stop <service-name>
```

Example:

```bash
sudo systemctl start nginx
```

### 2. Restarting and Reloading Services

```bash
sudo systemctl restart <service-name>     # Fully restarts the service
sudo systemctl reload <service-name>      # Reloads configuration without restarting (if supported)
```

### 3. Enabling and Disabling Services (at boot)

```bash
sudo systemctl enable <service-name>      # Start service automatically on boot
sudo systemctl disable <service-name>     # Disable service from starting at boot
```

### 4. Checking Service Status

```bash
systemctl status <service-name>
```

Example:

```bash
systemctl status ssh
```

### 5. Check if a Service is Enabled/Disabled

```bash
systemctl is-enabled <service-name>
```

### 6. Listing All Services

```bash
systemctl list-units --type=service
```

### 7. Listing All Loaded Units (services, sockets, devices, etc.)

```bash
systemctl list-units
```

### 8. Rebooting or Shutting Down

```bash
sudo systemctl reboot
sudo systemctl poweroff
```

### 9. Daemon Reload

If you change a unit file or add a new one:

```bash
sudo systemctl daemon-reexec     # Reexecutes systemd itself
sudo systemctl daemon-reload     # Reloads unit files without restarting systemd
```


---

## References

