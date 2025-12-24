# snort3-custom-rules
Custom Snort 3 rules for lab detection (SQLi, scans, brute-force spikes, flooding)
md
# Snort 3 Custom Rules (Portfolio / Lab) — Mujahid Ali Khan K

This repository contains a **lab-focused set of 25 custom Snort 3 rules** aligned to SOC Analyst / Detection Engineer use cases. The rules are designed to detect common network and web attack patterns and to demonstrate rule authoring, tuning, and validation in a controlled environment.

## What’s Included
All custom rules are in:
- `rules/local.rules`

Coverage areas:
- **SQL Injection (SQLi)** indicators in HTTP URI / body (e.g., `UNION SELECT`, `' OR 1=1`, `information_schema`, time-based SQLi)
- **Recon / Port scans** (threshold-based SYN/UDP spikes)
- **Brute-force indicators** (heuristic connection spikes to SSH/FTP/RDP)
- **DoS / Flooding** (SYN flood and ICMP echo flood heuristics)
- **Web probing** (e.g., `/admin`, `/.git`, `/phpmyadmin`, traversal patterns)
- **Suspicious scanner User-Agents** (e.g., `sqlmap`, `nikto`)

## Intended Use
- Portfolio demonstration of **custom detection content** and rule-writing fundamentals
- Validation using **authorized lab traffic only**
- These rules may require **threshold tuning** for your specific environment to reduce false positives

## How to Use (Snort 3)
1. Copy the rules file to your rules directory, for example:
   - `/usr/local/etc/rules/local.rules`

2. Ensure your Snort configuration (`snort.lua`) defines network variables appropriately:
   - `HOME_NET` should match your lab subnet (e.g., `192.168.56.0/24`)
   - `EXTERNAL_NET` can be `any` in a lab

3. Run Snort with the custom rules and fast alerts (example):
```bash
sudo snort -c /usr/local/etc/snort/snort.lua \
  -R /usr/local/etc/rules/local.rules \
  -i <interface> \
  -A alert_fast \
  -l /var/log/snort
