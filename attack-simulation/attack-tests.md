# Attack Simulation Guide

## Overview

This section demonstrates how different cyber attacks were simulated in a controlled lab environment to test the effectiveness of the Cowrie and Pentbox honeypots.

The attacker machine was used to generate reconnaissance scans and login attempts to observe how the honeypots capture malicious activity.

---

# 1. Port Scanning using Nmap

Attackers usually begin with reconnaissance to identify open ports and services.

Command used:

```bash
nmap -p- <honeypot-ip>
```

Purpose:
- Scan all ports on the honeypot system
- Trigger Pentbox honeypot detection

Expected Result:
Pentbox logs intrusion attempts and displays attacker IP and connection details.

---

# 2. SSH Login Attempt Simulation

Cowrie listens on port **2222** instead of the normal SSH port.

Command used:

```bash
ssh root@<honeypot-ip> -p 2222
```

Example passwords tested:

```
123456
admin
password
toor
root
```

Purpose:
- Simulate brute-force login attempts
- Observe how Cowrie logs usernames and passwords.

---

# 3. Command Execution Simulation

Once the attacker logs into the fake shell, common Linux commands are executed.

Example commands:

```
ls
pwd
whoami
uname -a
cat /etc/passwd
```

Purpose:
- Capture attacker behavior
- Analyze commands attackers typically execute after gaining access.

Cowrie records every command inside its log files.

---

# 4. Directory Navigation

Attackers often explore the system to understand its structure.

Commands used:

```
cd /
cd home
cd root
```

Purpose:
Observe attacker exploration patterns inside the honeypot.

---

# 5. Suspicious Network Activity

Some attackers attempt to download malicious files.

Example commands:

```
wget http://example.com
curl http://test.com
```

These commands do not execute fully in Cowrie but are logged for analysis.

---

# Outcome

The honeypot successfully captured:

- Attacker IP addresses
- Login attempts
- Password guesses
- Commands executed
- Reconnaissance scans

These logs help security researchers understand attacker behavior and improve defensive strategies.
