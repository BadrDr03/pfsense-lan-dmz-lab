# Validation plan

All rows below are pending unless explicitly marked observed. Record timestamp, source, destination, command, result, and screenshot/log filename for each test.

| ID | Test | Expected result | Current result |
|---|---|---|---|
| V01 | Ubuntu: ip -br a | enp0s3 UP, 192.168.20.10/24 | Observed; screenshot attached |
| V02 | Ubuntu: ip route | default via 192.168.20.1 | Observed; screenshot attached |
| V03 | Ubuntu resolver configuration and DNS query | Uses approved resolver; name resolves | Pending |
| V04 | Ubuntu package index update | Approved repositories reachable | Pending |
| V05 | Nginx service status and local HTTP request | Service active; expected page returned | Pending |
| V06 | LAN client HTTP request to 192.168.20.10 | Expected page returned | Pending |
| V07 | DMZ initiates connection to a known listening LAN test service | Blocked; matching firewall log | Pending |
| V08 | DMZ attempts firewall HTTPS management | Blocked; matching firewall log | Pending |
| V09 | DMZ uses an unapproved DNS resolver | Blocked | Pending |
| V10 | DMZ attempts an unapproved external service | Blocked | Pending |
| V11 | Inspect replies to allowed LAN-to-DMZ web requests | Replies pass through established state | Pending |
| V12 | Reboot Ubuntu and pfSense; repeat key checks | Addresses and policy persist | Pending |

For negative tests, first establish that the destination service is listening and reachable from an authorized source. A timeout alone does not prove firewall enforcement. Correlate the attempt with firewall logs and, if needed, a narrowly filtered capture. A blocked ping does not by itself prove web traffic is blocked. Use only lab-owned destinations or approved test endpoints.

Future evidence: firewall rule order, rule counters, DNS answer, successful package update, Nginx status, HTTP response, blocked-flow log, state table, and filtered packet capture. Do not upload authentication traffic or unsanitized packet captures.
