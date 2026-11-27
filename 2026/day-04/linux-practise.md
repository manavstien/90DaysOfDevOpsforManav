# Day 04 – Linux Practice: Processes and Services

## 1. Process Checks

### Command 1: `ps aux`

**Purpose:** Display all running processes.

**Observation:**
- The command displayed processes belonging to both `root` and my user.
- Multiple Brave browser processes were visible.
- Some Brave processes showed relatively high CPU usage at the time of inspection.
- Kernel threads such as `kthreadd` and `kworker` were also visible.

### Command 2: `ps -p $$ -o pid,ppid,comm`

**Purpose:** Inspect the current shell process.

**Observed output:**

| PID | PPID | COMMAND |
|---:|---:|---|
| 6141 | 6114 | bash |

**Observation:** My current Bash process had PID 6141 and parent process ID 6114.

### Command 3: `pgrep -a cron`

**Purpose:** Find the Cron process and display its command line.

**Observed output:**

```text
1477 /usr/sbin/cron -f -P
```

**Observation:** The Cron process was running with PID 1477.

---

## 2. Service Checks

### Command 4: `systemctl list-units --type=service --state=running`

**Purpose:** List currently running systemd services.

**Observation:** Several services were running, including:

- `cron.service`
- `cups.service`
- `NetworkManager.service`
- `rsyslog.service`
- `snapd.service`
- `snap.jenkins.jenkins.service`

I selected `cron.service` for further inspection.

### Command 5: `systemctl status cron`

**Purpose:** Inspect the status and details of the Cron service.

**Observed results:**

| Field | Value |
|---|---|
| Service | cron.service |
| Loaded | loaded |
| Enabled | enabled |
| Active | active (running) |
| Main PID | 1477 |
| Tasks | 1 |
| Memory | 508K |
| CPU time | 12ms |

**Observation:** Cron was enabled and running successfully.

---

## 3. Log Checks

### Command 6: `sudo journalctl -u cron.service -n 20`

**Purpose:** Display the latest 20 log entries for Cron.

**Observations:**
- Cron started successfully on 27 November 2026.
- The logs showed `Running @reboot jobs`.
- A warning appeared about the unset `EXTRA_OPTS` environment variable.

Warning observed:

```text
Referenced but unset environment variable evaluates
to an empty string: EXTRA_OPTS
```

The warning did not prevent the service from starting.

### Command 7: `sudo journalctl -u cron.service -f`

**Purpose:** Follow Cron logs in real time.

**Observation:** I saw the service startup messages and Cron informational logs. I stopped live monitoring using `Ctrl+C`.

---

## 4. Additional Check

### Command 8: `crontab -l`

**Purpose:** List scheduled Cron jobs for the current user.

**Observed output:**

```text
no crontab for manav
```

**Observation:** My user account did not have a personal crontab configured.

---

## 5. Mini Troubleshooting Flow

**Scenario:** A scheduled backup script is not executing.

Steps followed:

1. Check whether Cron is running:

   ```bash
   systemctl status cron
   ```

2. Inspect recent Cron logs:

   ```bash
   sudo journalctl -u cron.service -n 50
   ```

3. Verify that the Cron process exists:

   ```bash
   pgrep -a cron
   ```

4. Check scheduled jobs for the current user:

   ```bash
   crontab -l
   ```

**Conclusion:**

The Cron service was enabled and active. Its process was running with PID 1477. The logs showed a successful startup, along with an `EXTRA_OPTS` environment-variable warning. My user account had no personal Cron jobs configured.

This exercise helped me understand how to inspect Linux processes, check systemd service status, investigate service logs and perform basic troubleshooting.

---

**Day 04 Status: Completed**

Topics practised:
- Process inspection
- systemd service management
- Service log investigation
- Basic troubleshooting
