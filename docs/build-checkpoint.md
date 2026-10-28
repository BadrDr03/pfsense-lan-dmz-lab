# Build checkpoint — 28 October 2026

## Installed environment

- pfSense CE 2.9.0-RELEASE amd64; web administration accessed from the LAN and initial password changed privately.
- WAN adapter 1: NAT / em0; DHCP address observed 10.0.2.15, upstream gateway 10.0.2.2.
- LAN adapter 2: Internal Network FW-LAN / em1; 192.168.1.1/24; DHCP pool 192.168.1.100–192.168.1.199.
- DMZ adapter 3: Internal Network FW-DMZ / em2; 192.168.20.1/24. DMZ DHCP was not enabled.
- Kali client is a linked clone of an existing Kali VM. It depends on the original base disk; do not delete the base VM files.
- Ubuntu WEB01-DMZ uses a single adapter on FW-DMZ; enp0s3 is UP, 192.168.20.10/24, default route 192.168.20.1.
- Ubuntu installer was configured with DNS 1.1.1.1; runtime resolver configuration still needs verification.

## Next session

1. Start FW01-pfSense, CLIENT-FW-LAN, and WEB01-DMZ.
2. From the LAN client, open https://192.168.1.1.
3. Inspect Firewall > Rules > DMZ before changing rules. Save an initial local backup; do not publish an unsanitized export.
4. Add internal-destination protection, then narrowly scoped DNS and package access. Apply changes and verify rule order.
5. Verify Ubuntu DNS and outbound access, update packages, and install Nginx.
6. Implement the approved LAN web access rule and execute the validation matrix.

No custom DMZ rule list has yet been captured. Do not describe the final policy as deployed until it is reviewed and tested.
