# Test Case (Placeholder): SQL Injection Indicators (HTTP)

## Goal
Validate the SQLi indicator rules in `rules/local.rules` (URI/body patterns such as `UNION SELECT`, `' OR 1=1`, `information_schema`, and time-based SQLi keywords).

## Lab Setup (planned)
- Sensor: Ubuntu 20.04 running Snort 3 on the lab interface
- Attacker: Kali Linux (or any Linux host with curl)
- Victim: a lab HTTP service
  - Simple option: `python3 -m http.server 80`
  - Better option: DVWA or OWASP Juice Shop (lab-only)

## Commands (Attacker)
```bash
curl "http://<victim_ip>/?id=1%27%20OR%201%3D1--"
curl "http://<victim_ip>/?q=union%20select%201,2,3"
curl "http://<victim_ip>/?db=information_schema"
curl "http://<victim_ip>/?t=sleep(5)"
