# Pentbox Honeypot Setup Guide

## Overview

Pentbox is a lightweight security toolkit that includes a simple network honeypot.

It detects:

- Port scanning
- Unauthorized connections
- Intrusion attempts

---

# Step 1: Clone Pentbox

```bash
git clone https://github.com/technicaldada/pentbox.git
cd pentbox/pentbox-1.8
```

---

# Step 2: Run Pentbox

```bash
sudo ruby pentbox.rb
```

---

# Step 3: Enable Honeypot Mode

Select the following options:

```
2 → Network Tools
3 → Honeypot
1 → Fast Auto Configuration
```

---

# Step 4: Choose Listening Port

Example:

```
80
```

Output:

```
HONEYPOT ACTIVATED ON PORT 80
```

Pentbox will now monitor incoming connections.

---

# Step 5: Test Honeypot

From another terminal run:

```bash
nmap <honeypot-ip>
```

Pentbox will display:

```
INTRUSION ATTEMPT DETECTED
```

Captured data includes:

- Source IP
- Port number
- Time of attack
