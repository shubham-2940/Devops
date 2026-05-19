# Day 04 – Linux Practice: Processes and Services

## Objective

Today I practiced Linux fundamentals related to:
- Process management
- Service management
- Log inspection
- Basic troubleshooting

---

# 1. Process Checks

## Command 1 — View Running Processes

```bash
ps aux | head
```

### Observation
- Displayed currently running processes
- Observed PID, CPU usage, memory usage and commands

---

## Command 2 — Real Time Process Monitoring

```bash
top
```

### Observation
- Observed live CPU and memory usage
- Identified highest memory consuming process
- Pressed `q` to exit

---

## Command 3 — Run Process in Background

```bash
sleep 500 &
```

### Observation
- Process started in background
- Shell returned a Job ID and PID

Example:
```bash
[1] 2456
```

---

## Command 4 — Check Background Jobs

```bash
jobs
```

### Observation
- Displayed running background jobs

Example:
```bash
[1]+ Running sleep 500 &
```

---

## Command 5 — Bring Background Process to Foreground

```bash
fg
```

### Observation
- Background process moved to foreground terminal

---

## Command 6 — Search Process by Name

```bash
pgrep bash
```

### Observation
- Displayed PID of bash process

---

## Command 7 — Kill Process Safely

```bash
kill PID
```

Example:
```bash
kill 2456
```

### Observation
- Successfully terminated process

---

# 2. Service Checks

## Command 8 — Check SSH Service Status

```bash
systemctl status ssh
```

### Observation
- Verified ssh service is active and running

Example:
```bash
Active: active (running)
```

---

## Command 9 — List Running Services

```bash
systemctl list-units --type=service --state=running
```

### Observation
- Displayed all active services
- Observed services like:
  - ssh
  - cron
  - NetworkManager

---

## Command 10 — Start SSH Service

```bash
sudo systemctl start ssh
```

### Observation
- SSH service started successfully

---

## Command 11 — Enable SSH Service at Boot

```bash
sudo systemctl enable ssh
```

### Observation
- SSH service enabled during system startup

---

# 3. Log Checks

## Command 12 — Check SSH Logs

```bash
journalctl -u ssh --no-pager | tail -n 10
```

### Observation
- Viewed latest SSH service logs
- Verified login and startup logs

---

## Command 13 — View System Logs

```bash
tail -n 20 /var/log/syslog
```

### Observation
- Displayed recent system log entries

---

## Command 14 — Check Detailed System Logs

```bash
journalctl -xe
```

### Observation
- Viewed detailed system and service error logs

---

# 4. User and Permission Practice

## Command 15 — Create User

```bash
sudo useradd thor
```

### Observation
- Created new user named thor

---

## Command 16 — Set Password for User

```bash
sudo passwd thor
```

### Observation
- Password assigned successfully

---

## Command 17 — Switch User

```bash
su - thor
```

### Observation
- Switched from current user to thor user

---

## Command 18 — Create Directory

```bash
mkdir Appserver3
```

### Observation
- Created directory successfully

---

## Command 19 — Change Ownership

```bash
sudo chown thor:thor Appserver3
```

### Observation
- Ownership transferred to thor user

---

## Command 20 — Check Permissions

```bash
ls -l
```

### Observation
- Verified file and directory permissions

---

# 5. Mini Troubleshooting Steps

## Problem
Permission denied error occurred while accessing Appserver3 directory.

---

## Troubleshooting Commands

```bash
ls -l
sudo chown thor:thor Appserver3
chmod 755 Appserver3
su - thor
cd Appserver3
```

---

## Resolution

- Checked directory permissions
- Changed ownership to correct user
- Updated permissions
- Successfully accessed directory after fixing permissions

---

# Summary

Today I practiced:
- Process monitoring using ps, top, jobs, pgrep
- Background and foreground process handling
- Killing processes safely
- Service management using systemctl
- Viewing logs using journalctl and tail
- User management and permissions
- Basic Linux troubleshooting

This practice improved my understanding of Linux fundamentals required for DevOps.
