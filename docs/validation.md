# Lesson 3 — Validation results

Core lab validation completed on 1 November 2026. **Screenshot-backed** means a real image is included. **Operator-confirmed** means the command result was reported in the walkthrough but no screenshot of that exact output was supplied. Neither category implies an exhaustive security audit.

| ID | Run from | Command / check | Actual result | Evidence |
|---|---|---|---|---|
| V01 | Ubuntu | `ip -br a` and `ip route` | 192.168.20.10/24; gateway 192.168.20.1 | Screenshot |
| V02 | Ubuntu | `resolvectl query archive.ubuntu.com` | Name resolved | Screenshot |
| V03 | Ubuntu | `sudo apt update`; install Nginx | Package index update reported; Nginx installed | Operator report + service screenshot |
| V04 | Ubuntu | `systemctl status nginx`; `curl -I http://localhost` | Active/enabled; HTTP 200 | Screenshots |
| V05 | Kali | `curl -I --connect-timeout 5 http://192.168.20.10` | HTTP 200 | Screenshot |
| V06 | Kali | `ping -c 4 -W 2 192.168.20.10` | 4 sent, 0 received; LAN block rule matched | Terminal + firewall screenshots |
| V07 | Ubuntu | `ping -c 4 -W 2 192.168.1.100` | 4 sent, 0 received reported; DMZ-to-LAN block matched | Four ICMP block log entries |
| V08 | Ubuntu | `curl -k -I --connect-timeout 5 https://192.168.20.1` | Timeout; firewall-self block matched | Terminal + TCP SYN block logs |
| V09 | Kali | `ssh badr@192.168.20.10` | Logged into Ubuntu | Operator-confirmed; service and rule screenshots |
| V10 | Ubuntu | `sudo nginx -t` | Syntax OK, test successful | Screenshot |
| V11 | Kali | `curl -k -I --connect-timeout 5 https://192.168.20.10` | HTTP 200 | Operator-confirmed |
| V12 | Kali | `curl --cacert ~/web01-dmz.crt -I --connect-timeout 5 https://192.168.20.10` | HTTP 200 without bypassing certificate checks | Operator-confirmed |
| V13 | pfSense | Firewall > NAT > Outbound | Automatic rules include LAN and DMZ | Screenshot |
| V14 | Ubuntu | `curl -I --connect-timeout 5 --max-time 15 https://example.com` | HTTP 200 | Operator-confirmed |

## Reading the blocked-flow evidence

The DMZ-to-LAN logs show source **192.168.20.10**, destination **192.168.1.100**, protocol **ICMP**, and rule **Block DMZ to LAN - log attempts**. This establishes the firewall action for that ping test; it does not independently test every TCP or UDP service.

The firewall-management logs show **192.168.20.10:52000 → 192.168.20.1:443**, **TCP:S**, and **Block DMZ access to firewall - log attempts**. `S` means SYN, the initial TCP connection request. Repeated entries are retransmissions of that connection attempt. Combined with the curl timeout, these identify the block that caused the failure.

Successful LAN web and SSH sessions demonstrate that return traffic can pass in those sessions. The pfSense state table and a packet trace were not separately captured.

## Optional extensions — not required for this completed core lab

A controlled TCP service on the LAN for another negative test; an unapproved DNS-resolver test; an unapproved external-service test; a full post-TLS reboot validation; a packet capture; DHCP reservation for the administrator; and a separately designed IPv6 policy. None is claimed as completed.
