# 🔐 Cybersecurity — Zero to Hero (Self-Study Guide)

> Practical-only learning path. No theory grinding. All free resources.
> Built for someone with an IT background transitioning into cybersecurity remotely from the Netherlands.

---

## 🛠️ Setup (One Time)

### Tools to install
| Tool | Purpose | Where |
|---|---|---|
| VirtualBox | Run virtual machines | Main machine |
| Kali Linux | Hacking OS (runs inside VirtualBox) | VirtualBox |
| Burp Suite Community | Web hacking proxy tool | Main machine |

### Accounts to create (all free)
- [ ] portswigger.net/web-security — main lab platform
- [ ] hackthebox.com — real machines to hack
- [ ] github.com — portfolio + writeups
- [ ] linkedin.com — Dutch recruiters live here
- [ ] picoctf.org — beginner CTF competitions
- [ ] cyberdefenders.org — blue team / SOC challenges
- [ ] blueteamlabs.online — incident response labs
- [ ] overthewire.org — Linux command line as a game

---

## 📍 Phase 1 — First Hacks: PortSwigger SQL Injection

**Platform:** portswigger.net/web-security/all-labs (filter: Apprentice)
**Tool:** Burp Suite built-in browser (Proxy → Open browser)

### How to approach every lab
1. Open the lab
2. Try to solve it yourself first
3. Get stuck → search YouTube: `"PortSwigger [lab name] walkthrough"`
4. Solve it, then write a short note below

---

### SQL Injection Labs

#### ✅ Lab 1 — Hidden data retrieval
**URL:** `/filter?category=Gifts'--`
**What it does:** The `'` breaks the SQL query, `--` comments out the rest
**Result:** Shows hidden/unreleased products in the database

---

#### ✅ Lab 2 — Login bypass
**Where:** Username field on the login form (not the URL bar)
**Payload:** Username: `administrator'--` / Password: `anything`
**What it does:** The `--` comments out the password check in the SQL query
```sql
-- What the database sees normally:
SELECT * FROM users WHERE username='administrator' AND password='xyz'

-- What it sees after your injection:
SELECT * FROM users WHERE username='administrator'
-- password check is gone, you're in
```
**Result:** Logged in as administrator with no password ✅

---

#### ⬜ Lab 3 — UNION attack: number of columns
Technique: ' UNION SELECT NULL,NULL,NULL--
Keep adding NULL until page loads without error
Result: Query returns 3 columns 

---

#### ⬜ Lab 4 — UNION attack: finding a column with text
*Notes to fill in after completing*

---

#### ⬜ Lab 5 — UNION attack: retrieve data from other tables
*Notes to fill in after completing*

---

#### ⬜ Lab 6 — UNION attack: retrieve multiple values in single column
*Notes to fill in after completing*

---

## 📍 Phase 2 — XSS (Cross-Site Scripting)

*Start after completing SQL Injection Apprentice labs*

### What is XSS
You inject JavaScript code into a website that gets executed in the victim's browser.

### Labs (PortSwigger — Apprentice)
- [ ] Reflected XSS into HTML context with nothing encoded
- [ ] Stored XSS into HTML context with nothing encoded
- [ ] DOM XSS in document.write sink

*Add your notes and payloads here as you complete them*

---

## 📍 Phase 3 — Authentication

*Break login systems, bypass passwords, hijack sessions*

### Labs (PortSwigger — Apprentice)
- [ ] Username enumeration via different responses
- [ ] Password brute force via response timing
- [ ] 2FA simple bypass

*Add your notes and payloads here as you complete them*

---

## 📍 Phase 4 — Hack The Box (Real Machines)

**Starting Point track (free) — do in order:**
- [ ] Meow
- [ ] Fawn
- [ ] Dancing
- [ ] Redeemer
- [ ] Explosion

*For each machine, note: what ports were open, what exploit you used, how you got root*

---

## 📍 Phase 5 — VulnHub (Offline Machines)

**Recommended beginner machines (download, run in VirtualBox):**
- [ ] Kioptrix 1
- [ ] Mr. Robot
- [ ] DC-1

---

## 📍 Phase 6 — Blue Team / SOC Skills

### CyberDefenders (cyberdefenders.org)
- [ ] PacketMaze
- [ ] BlueSky
- [ ] *Add more as you complete them*

### Blue Team Labs Online (blueteamlabs.online)
- [ ] Getting Started labs
- [ ] *Add more as you complete them*

### OverTheWire — Linux skills as a game
- [ ] Bandit Level 0
- [ ] Bandit Level 1–5
- [ ] Bandit Level 6–10
- [ ] *Continue...*

---

## 🎓 Free Certifications (when ready)

| Cert | Where | Cost | Status |
|---|---|---|---|
| ISC2 Certified in Cybersecurity (CC) | isc2.org | Free training / ~€185 exam | ⬜ |
| Cisco CyberOps Associate | netacad.com | Free | ⬜ |
| Google Cybersecurity Certificate | Coursera (audit free) | Free to audit | ⬜ |

---

## 🧠 Key Concepts Learned So Far

### SQL Injection
- `'` — breaks the SQL query
- `--` — comments out everything after it (MySQL/MSSQL)
- `#` — comments out everything after it (MySQL alternative)
- Login bypass: inject into username field, not the URL
- POST forms ≠ GET URL parameters — always inject in the form field

*Add new concepts here as you learn them*

---

## 🏆 CTF Participation

| Event | Platform | Date | Challenges solved |
|---|---|---|---|
| | picoctf.org | | |
| | ctftime.org events | | |

---

## 💼 Job Targets (Netherlands — Remote)

| Company | Role | Applied | Notes |
|---|---|---|---|
| Fox-IT | Junior SOC / Pentest | ⬜ | Leading Dutch security firm |
| Northwave | SOC Analyst | ⬜ | Incident response focused |
| Computest | Junior Pentester | ⬜ | Pentest focused |
| KPN Security | SOC Analyst | ⬜ | Large SOC, often remote |
| Capgemini NL | Security Analyst | ⬜ | Junior tracks available |
| Thales NL | Security Engineer | ⬜ | Large corp, multiple roles |

---

## 📅 Timeline

| Month | Goal |
|---|---|
| 1 | PortSwigger SQL Injection + XSS Apprentice labs done |
| 2 | Authentication labs + first CTF + HTB Starting Point |
| 3 | VulnHub machines + GitHub writeups building up |
| 4 | Blue Team labs + CyberDefenders cases |
| 5 | ISC2 CC prep + start applying to junior roles |
| 6 | Actively interviewing |

---

## 📝 Useful Payloads Reference

### SQL Injection
```sql
'--                          -- comment out rest of query
' OR 1=1--                   -- always true condition  
' OR '1'='1                  -- alternative always true
admin'--                     -- login bypass (username field)
' UNION SELECT NULL--        -- start of UNION attack
```

### XSS
```javascript
<script>alert(1)</script>           -- basic test
<img src=x onerror=alert(1)>        -- img tag bypass
<svg onload=alert(1)>               -- svg bypass
```

*Add more as you discover them in labs*

---

## 🔗 Quick Links

- All labs: portswigger.net/web-security/all-labs
- HTB Starting Point: app.hackthebox.com/starting-point
- VulnHub: vulnhub.com
- CTF calendar: ctftime.org
- YouTube walkthroughs: search "IppSec" or "John Hammond"

---

*Last updated: ongoing*
