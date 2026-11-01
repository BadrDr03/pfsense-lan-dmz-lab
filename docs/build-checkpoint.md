# Final checkpoint — 1 November 2026

**Core lab complete.** Firewall segmentation rules, Nginx HTTP/HTTPS, SSH administration and automatic outbound NAT are configured. The [validation results](validation.md) distinguish screenshots from operator confirmations.

## Current environment

- pfSense CE 2.9.0-RELEASE amd64: em0 WAN DHCP 10.0.2.15/24; em1 LAN 192.168.1.1/24; em2 DMZ 192.168.20.1/24.
- LAN DHCP pool: 192.168.1.100–192.168.1.199. Kali was confirmed at .100 on 1 November.
- WEB01-DMZ: Ubuntu Server, enp0s3 192.168.20.10/24; gateway .20.1; configured resolver 1.1.1.1.
- Nginx serves the welcome page on 80 and 443. The TLS configuration is `/etc/nginx/conf.d/web01-https.conf`.
- Certificate: `/etc/ssl/certs/web01-dmz.crt`; private key: `/etc/ssl/private/web01-dmz.key` (600). The key is not stored in this repository.
- SSH is active/enabled. The firewall permits TCP 22 from Kali .1.100 to WEB01 .20.10.
- DMZ policy: block LAN; allow WEB01 DNS to 1.1.1.1; block firewall-self access; allow WEB01 TCP 80/443 egress.
- Automatic outbound NAT includes both LAN and DMZ.

## Resume or demonstrate

Start pfSense first, then Kali and Ubuntu. Verify Kali's address with `ip -4 addr show eth0`; the SSH rule depends on .100. Open pfSense from Kali at `https://192.168.1.1`. Use `ssh badr@192.168.20.10` to administer Ubuntu, or run the validation commands from the appropriate machine.

For shutdown, use `sudo poweroff` on Ubuntu and Kali, then **Diagnostics > Halt System** on pfSense. A reboot regression after the final TLS changes has not been recorded.

## Earlier checkpoint

On 28 October only the infrastructure and static server networking were complete. Subsequent sessions added the firewall rules, Nginx, log validation, SSH and TLS. The original architecture/policy PNGs remain as historical illustrations; use the current README diagram and firewall-policy tables for the final configuration.
