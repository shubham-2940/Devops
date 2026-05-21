# linux-troubleshooting-runbook.md

# Day 05 – Linux Troubleshooting Drill

## Target Service / Process

Service chosen: `ssh`

### Purpose

The SSH service allows secure remote access to the Linux system.
This troubleshooting drill focuses on checking system health, network connectivity, disk usage, memory usage, and service logs related to SSH.

---

# 1. Environment Basics

## Command 1

```bash
uname -a

```

### Observation

Displayed Linux kernel version, architecture, and system details.
Confirmed Ubuntu Linux is running inside VirtualBox.

---

## Command 2

```bash
cat /etc/os-release
```

### Observation

Verified Ubuntu distribution name and release version.

---

# 2. Filesystem Sanity Check

## Command 3

```bash
mkdir /tmp/runbook-demo
```

### Observation

Created a temporary directory successfully for troubleshooting practice.

---

## Command 4

```bash
cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo
```

### Observation

Copied the hosts file successfully and verified permissions using `ls -l`.

---

# 3. CPU & Memory Snapshot

## Command 5

```bash
top
```

### Observation

Observed active system processes and CPU usage.
System load appeared stable with no unusual CPU spikes.

---

## Command 6

```bash
free -h
```

### Observation

Checked available and used memory.
System had sufficient free memory and no swap pressure.

---

## Command 7

```bash
ps -o pid,pcpu,pmem,comm -C sshd
```

### Observation

Verified SSH daemon resource usage.
CPU and memory utilization were minimal.

---

## Command 8

```bash
vmstat 1 5
```

### Observation

Monitored CPU, memory, swap, and IO activity.
No high IO wait or memory bottleneck was observed.

---

# 4. Disk & IO Snapshot

## Command 9

```bash
df -h
```

### Observation

Checked filesystem disk usage.
Root partition had sufficient free space available.

---

## Command 10

```bash
du -sh /var/log
```

### Observation

Verified total size of log directory.
No abnormal log growth was detected.

---

## Command 11

```bash
iostat
```

### Observation

Observed disk read/write statistics and CPU IO usage.
Disk activity was within normal range.

---

## Command 12

```bash
dstat
```

### Observation

Monitored real-time CPU, disk, and network activity together.
System performance remained stable during monitoring.

---

# 5. Network Snapshot

## Command 13

```bash
ss -tulpn | grep ssh
```

### Observation

Verified SSH service is actively listening on port 22.

---

## Command 14

```bash
curl -I http://localhost
```

### Observation

`curl` failed to connect to localhost on port 80 because no web server was running.
This confirmed that no HTTP service was active on the system.

---

## Alternative Network Verification

```bash
nc -zv localhost 22
```

### Observation

Successfully verified that SSH service is reachable locally on port 22.

---

# 6. Logs Reviewed

## Command 15

```bash
journalctl -u ssh -n 50
```

### Observation

Reviewed the last 50 SSH service logs.
No recent authentication failures or service crashes were found.

---

## Command 16

```bash
tail -n 50 /var/log/syslog
```

### Observation

Checked recent system log entries.
No critical system errors related to SSH were detected.

---

# Quick Findings

* SSH service is active and listening on port 22.
* CPU and memory usage are stable.
* Disk usage is healthy with enough free space.
* No excessive IO wait or swap activity detected.
* System logs do not show critical SSH-related issues.
* No local web server is running on port 80.

---

# Understanding Monitoring Commands

## iostat

Used to monitor CPU utilization and disk Input/Output statistics.

### Common Usage

```bash
iostat
```

### Purpose

* Detect disk bottlenecks
* Monitor disk read/write activity
* Analyze IO performance

---

## vmstat

Used to monitor virtual memory, processes, CPU, and IO.

### Common Usage

```bash
vmstat 1 5
```

### Purpose

* Check memory pressure
* Detect swap usage
* Monitor CPU wait time

---

## dstat

An all-in-one system resource monitoring tool.

### Common Usage

```bash
dstat
```

### Purpose

* Monitor CPU
* Monitor disk activity
* Monitor network traffic
* View live system performance

---

# If This Worsens (Next Steps)

## Step 1 — Restart SSH Service

```bash
sudo systemctl restart ssh
```

### Purpose

Restart SSH service if connectivity issues continue.

---

## Step 2 — Monitor Logs in Real Time

```bash
journalctl -u ssh -f
```

### Purpose

Track live SSH logs during troubleshooting.

---

## Step 3 — Advanced Process Investigation

```bash
strace -p <PID>
```

### Purpose

Trace SSH process system calls if the service becomes unresponsive.

---

# Conclusion

This troubleshooting drill helped practice:

* Linux system monitoring
* Service inspection
* Disk and memory analysis
* Network troubleshooting
* Log analysis
* Basic incident response workflow

The runbook can be reused during real Linux troubleshooting scenarios and future DevOps practice sessions.
