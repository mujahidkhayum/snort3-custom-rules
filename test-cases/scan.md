# Test Case (Placeholder): Recon / Port Scan Spike

## Goal
Validate the threshold-based scan detection rules in `rules/local.rules` (e.g., SYN scan spike).

## Lab Setup (planned)
- Sensor: Ubuntu 20.04 running Snort 3 on the lab interface
- Attacker: Kali Linux
- Victim: Ubuntu / test host with at least one TCP port open (e.g., 22/80)

## Command (Attacker)
```bash
nmap -sS -p 1-200 <victim_ip>
