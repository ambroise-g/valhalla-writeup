# Valhalla — TryHackMe Write-up

> **Difficulty:** Medium  
> **Category:** Linux · Web · Privilege Escalation  
> **Theme:** Norse Mythology  
> **Platform:** TryHackMe

---

## Overview

**Valhalla** is a Linux-based Capture The Flag room built around Norse mythology.  
The challenge focuses on chaining multiple misconfigurations across a Flask web application and the underlying system to escalate privileges from a remote attacker to root.

This write-up explains the intended attack path, techniques involved, and the logic behind each step, while keeping an educational and reviewer-friendly approach.

---

## Attack Path Summary

1. **Initial Enumeration**
   - Service discovery with `nmap`
   - Web content discovery with `ffuf`
   - Identification of a Flask application behind an Nginx proxy

2. **Web Analysis & Exploitation**
   - Session handling analysis
   - Flask cookie forging using a leaked secret
   - Server-Side Template Injection (SSTI)
   - Remote command execution as user **loki**

3. **Post-Exploitation & Local Enumeration**
   - Discovery of additional users: `fenrir`, `jormungandr`, `odin`
   - Identification of writable IPC mechanisms and group permissions
   - Enumeration with `linpeas`

4. **Privilege Escalation Chain**
   - **Jormungandr:** Abusing a writable Unix socket connected to a logging system
   - **Fenrir:** Leveraging group permissions and Apache misconfiguration
   - **Odin:** Debugging a running process via GDB to abuse internal `chmod` usage
   - **Root:** Final escalation via sudo privileges

---

## Key Techniques Used

- Flask session forging
- Server-Side Template Injection (SSTI)
- Unix domain sockets abuse
- Group permission abuse
- Local web server exploitation
- GDB process introspection
- Privilege escalation via misconfigured sudo rules

---

## Repository Contents

- `Writeup.pdf` — A fully detailed and illustrated write-up (step-by-step)
- `README.md` — Overview and methodology (this file)

---

## Notes for Reviewers

- This room is **not intended to be fully realistic**
- It is designed as a learning-focused CTF
- Each privilege escalation step highlights a distinct class of misconfiguration
- The attack path is linear and intentional

Payloads and commands are explained conceptually to avoid unnecessary copy-paste exploitation.

---

## Lessons Learned

This project was built as a learning experience and combines:
- Web exploitation
- Linux internals
- Privilege escalation patterns
- Lore-driven challenge design

The room reflects techniques discovered and practiced during the learning process.

---

## Conclusion

Valhalla is a technical journey through misconfigurations, logic flaws, and trust abuses — where **knowledge matters more than strength**.

Feedback and suggestions are always welcome.

---

*This write-up is provided for educational and review purposes only.*
