# Cowrie Honeypot Installation Guide

## Overview
Cowrie is a medium-interaction SSH/Telnet honeypot used to log attacker activity.

It records:
- Login attempts
- Password guesses
- Commands executed
- Session behavior

---

# Step 1: Create a Dedicated User

Running Cowrie as a non-root user improves security.

```bash
sudo adduser --disabled-password --gecos "" cowrie
sudo su - cowrie
```

---

# Step 2: Install Required Dependencies

```bash
sudo apt update
sudo apt install -y python3 python3-pip python3-venv git libssl-dev libffi-dev build-essential authbind
```

These packages are required for running Cowrie and its Python environment.

---

# Step 3: Download Cowrie

```bash
git clone https://github.com/cowrie/cowrie.git
cd cowrie
```

---

# Step 4: Create Virtual Environment

```bash
python3 -m venv cowrie-env
source cowrie-env/bin/activate
```

This isolates Cowrie dependencies from the system.

---

# Step 5: Install Requirements

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

# Step 6: Configure Cowrie

```bash
cp etc/cowrie.cfg.dist etc/cowrie.cfg
cp etc/userdb.example etc/userdb.txt
```

Add fake credentials:

```
root:x:password123
admin:x:admin123
test:x:test123
```

---

# Step 7: Start Cowrie

```bash
./cowrie-env/bin/cowrie start
```

Check service:

```bash
sudo ss -tulnp | grep 2222
```

---

# Step 8: View Logs

Cowrie logs are stored in:

```
var/log/cowrie/
```

Live log monitoring:

```bash
tail -f var/log/cowrie/cowrie.log
```

JSON structured logs:

```bash
jq . var/log/cowrie/cowrie.json
```

---

# Result

Cowrie will now capture:

- attacker IP address
- login attempts
- commands executed
- session behavior
