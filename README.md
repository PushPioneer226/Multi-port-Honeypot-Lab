# Multi‑port Honeypot Lab

A low‑interaction honeypot that monitors malicious activity across **multiple network ports**, simulating vulnerable services to attract and log attacks in real time.

## Purpose

This project was built to:
- Understand real‑world attack patterns on open ports
- Collect data on automated scanners, bots, and low‑skill attackers
- Learn how honeypots can be used for threat intelligence

## Technologies Used

| Category | Tools |
|----------|-------|
| Language | Python 3 |
| Networking | Socket programming, TCP/UDP |
| Logging | Custom JSON logs, Syslog |
| Deployment | Ubuntu Server / Raspberry Pi |
| Analysis | Jupyter Notebook / Pandas |

## Simulated Ports & Services

| Port | Simulated Service | What It Pretends To Be |
|------|-------------------|------------------------|
| 22 | SSH | OpenSSH 7.4 |
| 23 | Telnet | Cisco router |
| 80 | HTTP | Apache 2.4 |
| 443 | HTTPS | Nginx |
| 3306 | MySQL | MySQL 8.0 |
| 8080 | Proxy | Squid proxy |

## How It Works

```python
# Simplified logic example
for port in monitored_ports:
    listener = socket.socket()
    listener.bind(("0.0.0.0", port))
    listener.listen(5)
    # Log any connection attempt
    log_attack(source_ip, port, timestamp)

What I Logged
Each connection attempt captures:

Source IP address

Timestamp (UTC)

Target port

First 100 bytes of payload (if any)

Protocol (TCP/UDP)

How to Run This Yourself
# Clone the repository
git clone https://github.com/PushPioneer226/Multi-port-Honeypot-Lab.git
cd Multi-port-Honeypot-Lab

# Install dependencies
pip install -r requirements.txt

# Run the honeypot (requires sudo for ports below 1024)
sudo python3 honeypot.py

Sample Results
After running on a public VPS, the honeypot logged multiple connection attempts. Below is a screenshot of real‑time logs showing attacks on ports 22, 8080, and 3306.

https://honeypotlogs.jpg

Real‑time log showing connection attempts from different source IPs.

What I Learned
Most attacks target default service ports within minutes of going online

Automated scanners are the vast majority of traffic

Logging structure matters for later analysis

Running a honeypot requires careful isolation (don't use real credentials!)

Safety Disclaimer
⚠️ This honeypot was run in an isolated environment on a throwaway VPS. Do not run this on a production server or network you care about. All data collected was anonymous IP traffic with no interaction beyond connection logging.

Links
My LinkedIn Profile

Status
✅ Completed and tested
📝 Logs analyzed
🐍 Ready for extension (add more ports, geo‑IP mapping, email alerts)

