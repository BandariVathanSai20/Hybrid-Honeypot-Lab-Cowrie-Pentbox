# Log Analysis

## Overview

After deploying the Cowrie and Pentbox honeypots, multiple attack simulations were conducted to observe attacker behavior.

Both honeypots generated log files that contain valuable information about the attack attempts.

Cowrie stores logs in:

```
var/log/cowrie/
```

Main log files:

- cowrie.log
- cowrie.json

Pentbox logs intrusion attempts directly in the terminal output.

---

# Information Captured by Honeypots

The honeypot environment captured several types of attacker activity including:

- Attacker IP addresses
- Username attempts
- Password attempts
- Commands executed
- Port scanning behavior
- Session timestamps

---

# Example Cowrie JSON Log

Example log entry:

```json
{
  "timestamp": "2025-01-12T14:22:01",
  "src_ip": "192.168.1.20",
  "username": "root",
  "password": "123456",
  "command": "ls -la"
}
```

Explanation:

| Field | Description |
|------|-------------|
| timestamp | Time when attack occurred |
| src_ip | Attacker IP address |
| username | Username attempted |
| password | Password used in attack |
| command | Command executed by attacker |

---

# Most Common Username Attempts

During testing, the most frequently used usernames were:

- root
- admin
- test

These are common default usernames targeted during brute-force attacks.

---

# Most Common Password Attempts

Observed password attempts included:

- 123456
- password
- admin
- root

These passwords are frequently used in automated attack tools.

---

# Commands Executed by Attackers

Once access was gained to the fake shell, attackers attempted to gather system information.

Common commands observed:

```
ls
pwd
whoami
uname -a
cat /etc/passwd
```

Purpose of these commands:

- Explore system directories
- Identify system users
- Gather OS information

---

# Attack Behavior Pattern

Typical attack sequence observed:

1. Reconnaissance (Port Scanning)
2. SSH Login Attempts
3. Password Guessing
4. Command Execution
5. System Exploration

This behavior closely matches real-world attacker methodology.

---

# Security Insights

Based on the captured data, the following insights were observed:

- Weak passwords are the primary target of brute-force attacks
- Automated tools perform rapid login attempts
- Attackers attempt to gather system information immediately after login
- Honeypots are effective in capturing attacker techniques without risking real systems

---

# Conclusion

The honeypot environment successfully captured attacker activity and provided valuable insights into attack techniques and behavior patterns.

Analyzing these logs helps cybersecurity professionals strengthen security defenses and improve intrusion detection mechanisms.
